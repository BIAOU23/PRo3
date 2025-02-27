# Projet Analyse Statique

**COMPTE RENDU PROJET STATIC**

Ce dépôt contient l’ensemble des documents et scripts relatifs au projet d’analyse statique de vulnérabilités logicielles. Ce projet a été réalisé par l’équipe suivante :

- **BIAOU Afouda Jean Paul**
- **SIMPORE Idriss**
- **YA Roxane**

---

## Table des Matières

- [Introduction](#introduction)
- [Objectifs](#objectifs)
- [Prérequis](#prérequis)
- [Installation et Configuration](#installation-et-configuration)
- [Étapes de l’Analyse](#étapes-de-lanalyse)
  - [Exercice 1](#exercice-1)
  - [Exercice 2](#exercice-2)
- [Résultats et Conclusions](#résultats-et-conclusions)
- [Usage et Exploitation](#usage-et-exploitation)
- [Remerciements](#remerciements)

---

## Introduction

Ce projet a pour but d’effectuer une analyse statique des logiciels afin d’identifier des vulnérabilités potentielles. Les exercices réalisés incluent :
- L’importation et configuration d’un environnement virtuel (AVL-LAB.ova sous VirtualBox).
- L’analyse de fichiers exécutables avec des outils de décompression, mise à jour de VM et utilisation de services en ligne (VirusTotal).

---

## Objectifs

- **Analyser la sécurité des fichiers exécutables** : identifier s’ils correspondent à des signatures d’antivirus ou à des malwares connus.
- **Vérifier la compilation et le packing** : déterminer si les fichiers sont compressés ou s’ils présentent des vulnérabilités dues à l’ancienneté de leur compilation.
- **Étudier les API utilisées** : comprendre le comportement du fichier en fonction des fonctions importées et des chaînes de caractères présentes.

---

## Prérequis

- **VirtualBox** pour importer et exécuter le LAB virtuel (AVL-LAB.ova).
- Accès aux outils de décompression (exemple : `unzip`).
- Accès à [VirusTotal](https://www.virustotal.com) pour vérifier les fichiers exécutables.
- Environnement Linux pour la configuration réseau (`ifup`) et mise à jour de la VM (`fast-update install_avl`).

---

## Installation et Configuration

1. **Importation du LAB virtuel :**
   - Importez le fichier `AVL-LAB.ova` dans VirtualBox.
2. **Configuration de l'interface réseau :**
   - Exécutez la commande :
     ```bash
     sudo ifup enp0s3
     ```
3. **Décompression des fichiers :**
   - Utilisez la commande :
     ```bash
     unzip <nom_du_fichier.zip>
     ```
4. **Mise à jour de la VM :**
   - Exécutez la commande :
     ```bash
     fast-update install_avl
     ```

---

## Étapes de l’Analyse

### Exercice 1

1. **Analyse initiale des fichiers :**
   - Chargement des fichiers `ii.exe` et `tp1/lab0101.dll` sur [VirusTotal](https://www.virustotal.com).
   - Résultat : Correspondance avec une signature antivirus de malwares connus.
2. **Analyse de la compilation :**
   - Les fichiers ont été compilés pour la dernière fois le **19 Décembre 2010 à 17h16**.
   - **Observation :** Ces fichiers anciens pourraient présenter des vulnérabilités connues.
3. **Examen des API et des sections du fichier :**
   - Analyse des fonctions importées et des chaînes de caractères indique que le programme est destiné à s’exécuter sur un environnement Windows.
   - Le fichier n’est pas compressé (non "packed").

### Exercice 2

1. **Analyse du second fichier :**
   - Chargement du fichier `lab01-02.exe` sur VirusTotal.
   - Résultat : Correspondance avec une signature antivirus de malwares connus.
2. **Analyse similaire à l’Exercice 1 :**
   - Date/heure de compilation : **Mercredi 19 janvier 2011 à 17h10**.
   - **Packing :** Le fichier est initialement packé, puis décompressé pour une analyse approfondie.
   - Après décompression, le fichier n’est plus packé.
   - Les fonctions importées et chaînes de caractères confirment qu’il s’agit d’un programme Windows standard.

---

## Résultats et Conclusions

- **Antivirus et Malware :** Les fichiers analysés correspondent à des signatures d’antivirus de malwares connus.
- **Ancienneté des fichiers :** Les dates de compilation indiquent que les fichiers sont anciens, ce qui peut augmenter le risque de vulnérabilités de sécurité non corrigées.
- **Analyse des API :** Les fichiers interagissent avec le système Windows via des API classiques, suggérant des fonctionnalités standard de gestion de processus, de threads et de services.

---

## Usage et Exploitation

Ce dépôt peut être utilisé comme support pédagogique pour :
- La compréhension des techniques d’analyse statique.
- La mise en place d’un environnement de test en sécurité informatique.
- L’étude des différences entre fichiers packés et non packés.

Pour cloner ce dépôt :
```bash
git clone https://github.com/votre-utilisateur/projet-analyse-statique.git
