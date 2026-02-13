# TP2 : Prétraitement et Représentation de Données - IFT870

Ce projet a été réalisé dans le cadre du cours IFT870 - Forage de données.

**Auteurs :**
- Titouan CHOALER (chot4078)
- Ethan BROUILLET (broe5997)

## Description

L'objectif de ce deuxième travail pratique est d'explorer, de prétraiter et d'analyser un jeu de données sur les produits pharmaceutiques. Le processus complet inclut le chargement des données, le nettoyage, la fusion, la préparation des données, et finalement la modélisation pour prédire les classes pharmacologiques (`EPC`) d'un médicament.

Le compte rendu et le code du TP est contenu dans le notebook Jupyter `tp2.ipynb`
L'énoncé du TP est dans le fichier `TP2_sujet.pdf`.

## Données

Le projet s'appuie sur deux fichiers de données principaux :
- `product2.csv`: Contient des informations détaillées sur les produits (nom, substance, dosage, etc.).
- `package2.csv`: Contient des informations sur les emballages des produits (description, dates de commercialisation, etc.).

D'autres fichiers CSV (`_clean`, `_v2`, `merged.csv`) sont des versions intermédiaires ou finales générées durant le processus.

## Démarche

Le notebook suit une démarche structurée en 9 étapes principales :

1.  **Auscultation des données :** Analyse initiale de la structure, des types, et des valeurs manquantes.
2.  **Découverte de règles et relations :** Identification des dépendances fonctionnelles et des inclusions pour comprendre la structure des données.
3.  **Correction des erreurs :** Résolution des incohérences de format et des erreurs logiques (ex: dates invalides).
4.  **Traitement des valeurs manquantes et des doublons :** Imputation des données manquantes (par ex. pour `ROUTENAME`, `DEASCHEDULE`) et suppression des doublons.
5.  **Fusion des jeux de données :** Jointure interne des tables `product` et `package` sur `PRODUCTID` pour consolider les informations.
6.  **Simplification et préparation des données :**
    - **Parsing de `PHARM_CLASSES` :** Extraction des classes `EPC`, `MOA`, etc., dans des colonnes dédiées.
    - **Vectorisation :** Transformation des données textuelles et catégorielles en format numérique à l'aide de `TfidfVectorizer` (pour `SUBSTANCENAME`) et `OneHotEncoder` (pour `DOSAGEFORMNAME`, `ROUTENAME`).
7.  **Réduction des attributs :** Sélection des caractéristiques les plus pertinentes pour la modélisation et suppression des attributs redondants ou non informatifs (comme les identifiants ou les données administratives).
8.  **Modélisation :**
    - **Objectif :** Prédire la ou les classes `EPC` (Established Pharmacologic Class) pour chaque médicament.
    - **Modèle :** Un `RandomForestClassifier` a été choisi pour sa capacité à gérer la classification multi-label nativement et sa robustesse au sur-apprentissage. Un `GradientBoostingClassifier` a également été testé à des fins de comparaison.
    - **Métrique :** Le `F1-Score (micro)` a été utilisé pour évaluer la performance.
9.  **Résultats et Conclusion :**
    - Le modèle `Random Forest` a atteint un **F1-Score de 99.68%** sur l'ensemble de test.
    - Le temps d'entraînement était significativement plus rapide que le `Gradient Boosting` (33 secondes contre ~53 minutes).
    - Le modèle a ensuite été utilisé pour prédire les classes des produits où l'information était manquante, en utilisant les probabilités (`predict_proba`) avec un seuil ajusté pour garantir une prédiction pour chaque entrée.

## Dépendances

Pour exécuter le notebook, les bibliothèques Python suivantes sont nécessaires :
- `pandas`
- `numpy`
- `matplotlib`
- `seaborn`
- `scikit-learn`

Vous pouvez les installer via pip :
```bash
pip install pandas numpy matplotlib seaborn scikit-learn
```
