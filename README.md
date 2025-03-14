
# 🧪 TriMolDynamics : Simulation Numérique de la Dynamique d’une Molécule Triatomique  

Ce projet a pour objectif de **simuler la dynamique d’une molécule triatomique** en utilisant une **intégration numérique** des équations du mouvement grâce à **l’algorithme de Verlet**. Deux versions de simulation ont été développées :  

✅ **Simulation générique (`projet.py`)** : Permet de modéliser la dynamique d’une molécule triatomique sans nécessiter de fichier d’entrée. Une configuration initiale fixe est imposée.  
✅ **Simulation basée sur un fichier PDB (`projet_PDB.py`)** : Charge les coordonnées initiales d’une molécule triatomique à partir d’un fichier PDB (ex : cyclopropane) pour analyser sa dynamique réelle.  
📊 **Analyse des résultats (`plot_HO_MD.R`)** : Génère des graphiques et analyse l'évolution des énergies afin de vérifier la conservation de l’énergie du système.  

---

## 📁 Table des Matières
1. [Introduction](#introduction)  
2. [Détails des Fichiers et Fonctions](#détails-des-fichiers-et-fonctions)  
3. [Installation et Dépendances](#installation-et-dépendances)  
4. [Utilisation](#utilisation)  
5. [Analyse des Résultats](#analyse-des-résultats)  
6. [Améliorations Possibles](#améliorations-possibles)  
7. [Auteurs et Licence](#auteurs-et-licence)  

---

## 🎯 Introduction  

La simulation numérique joue un rôle crucial dans la compréhension des systèmes moléculaires en physique et en chimie. La dynamique moléculaire permet d’étudier l’évolution des **positions, vitesses et énergies** d’un système soumis à des forces internes et externes.  

L’objectif de ce projet est d’implémenter un **modèle simple de molécule triatomique** en utilisant un **potentiel harmonique** et d’étudier la conservation de l’énergie au fil du temps. L’intégration des équations du mouvement repose sur **l’algorithme de Verlet**, connu pour sa stabilité et son respect de la conservation énergétique.  

Nous avons développé **deux approches** :  
- **Une simulation générique** (`projet.py`), où la molécule est initialisée sous forme de **triangle équilatéral**.  
- **Une simulation basée sur un fichier PDB** (`projet_PDB.py`), permettant d’étudier une **molécule réelle issue de données expérimentales**.  

Enfin, un **script en R** (`plot_HO_MD.R`) a été conçu pour **analyser et visualiser** l’évolution des énergies **potentielle, cinétique et totale**, afin de vérifier la stabilité numérique de la simulation.

---

## 🖥️ Détails des Fichiers et Fonctions  

### 🔹 1. `projet.py` – Simulation Générique  

Ce script effectue une simulation de **dynamique moléculaire 2D** pour une molécule triatomique **sans fichier d’entrée**.  

#### **Fonctions principales :**  

| Fonction | Paramètres | Description |
|----------|------------|-------------|
| `potential_energy_total(positions)` | `positions` (array 2D) | Calcule l’énergie potentielle du système. |
| `compute_forces_numerical(positions)` | `positions` (array 2D) | Approximation des forces via différences finies. |
| `initial_velocities()` | Aucun | Génère des vitesses initiales selon la distribution de Maxwell-Boltzmann. |
| `start_Verlet(positions, velocities)` | `positions` (array 2D), `velocities` (array 2D) | Initialise Verlet en calculant la position précédente. |
| `do_MD(positions)` | `positions` (array 2D) | Lance la simulation et enregistre les énergies dans `RES.dat`. |

📌 **Résultats** : Une **animation 2D** montrant le mouvement des atomes et leur évolution temporelle.

---

### 🔹 2. `projet_PDB.py` – Simulation avec Fichier PDB  

Ce script charge les **coordonnées de trois atomes lourds** depuis un **fichier PDB** (ex : cyclopropane) et applique les mêmes algorithmes que `projet.py`.  

#### **Fonctions spécifiques :**  

| Fonction | Paramètres | Description |
|----------|------------|-------------|
| `load_pdb(filename)` | `filename` (str) | Extrait les **trois premiers atomes lourds (C, N, O, S)** depuis un fichier PDB. |

📌 **Résultats** :  
- **Permet d’utiliser des données expérimentales** pour la simulation.  
- **Compare l’évolution d’une molécule réelle** avec la version générique.  

---

### 🔹 3. `plot_HO_MD.R` – Analyse des Énergies  

Ce script en **R** analyse les données contenues dans `RES.dat` et **génère des courbes d’énergie** pour visualiser l’évolution du système.

#### **Fonctionnalités :**  
✔ Vérifie et nettoie les **données manquantes ou aberrantes**.  
✔ Trace les courbes **d’énergie potentielle (rouge), cinétique (vert) et totale (noir)**.  
✔ Ajoute une **ligne horizontale** pour indiquer l’énergie totale moyenne.  

📌 **Sortie** :  
📈 **Un fichier image `energies_oscillations.png` est généré** et sauvegardé.

---

## ⚙️ Installation et Dépendances  

### **Python**
Les scripts Python nécessitent **`numpy`** et **`matplotlib`** et le script R nécessite ggplot2 pour la visualisation :  
```bash
pip install numpy matplotlib
install.packages("ggplot2")
```

#### **🚀 Utilisation :** 

1️⃣ Exécuter la simulation sans fichier d’entrée
```bash
python projet.py
```

2️⃣ Exécuter la simulation avec un fichier PDB
⚠️ Assurez-vous que le fichier PDB est présent dans le répertoire.
```bash
python projet_PDB.py
```

3️⃣ Analyser les résultats avec R
📌 Un fichier energies_oscillations.png sera généré.
```bash
Rscript plot_HO_MD.R
```

#### **👨‍🔬 Auteurs et Licence :** 

📌 Auteur : MANOUR INES & BENHAMOUCHE SOFIA

📌 Date : Mars 2025

📌 Licence : Master 1 BioInformatique Université Paris Cité 

🚀 Projet Open-Source, modifications et contributions bienvenues !


