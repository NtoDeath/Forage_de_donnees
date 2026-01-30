# TP1 - Exploration de Données (IFT-870)

Ce projet a été réalisé dans le cadre du cours IFT-870 (Forage de données) de l'Université de Sherbrooke. Il s'agit d'un TP (TP1) centré sur l'exploration de données, incluant la visualisation, l'analyse de corrélation, la réduction de dimension et le choix d'une mesure de similarité.

## Membres de l'équipe

- Titouan CHOALER
- Ethan BROUILLET

## Description du projet

L'objectif principal de ce TP est de déterminer si les 4 attributs d'un jeu de données (`TP1_data.csv`) possèdent des propriétés discriminantes pour la classification de nouvelles observations. Pour cela, un modèle de classification basé sur la distance doit être développé et évalué.

Le notebook Jupyter (`tp1.ipynb`) met en œuvre les tâches suivantes :

### 1. Représentation des données
- **Analyse de corrélation** : Évaluation quantitative et visuelle des corrélations entre les 4 attributs pour déterminer la nécessité d'une Analyse en Composantes Principales (ACP).
- **Transformation ACP** : Si nécessaire, application de l'ACP et détermination du nombre optimal de composantes (2 ou 3) à utiliser pour la classification. Ce choix est validé en utilisant la méthode du plus proche centroïde avec la distance Euclidienne.

### 2. Choix de la mesure de distance
- **Évaluation des distances** : En se basant sur l'analyse de corrélation, sélection de la mesure de distance la plus adéquate parmi :
    - Manhattan
    - Euclidienne
    - **Mahalanobis**
    - Chebyshev
- **Distance de Mahalanobis** : Comparaison entre l'utilisation d'une matrice de covariance par classe et une matrice de covariance globale pour déterminer l'approche la plus pertinente.

### 3. Choix du modèle de classification
- **Comparaison de modèles** : Test de deux approches de classification basées sur la distance :
    - La méthode des **k=5 plus proches voisins (k-NN)**.
    - La méthode du **plus proche centroïde**.
- **Modèle de Mélange Gaussien (GMM)** : Test de l'hypothèse que les données sont générées par un mélange de distributions gaussiennes en appliquant un `Gaussian Mixture Model` et en justifiant le choix du type de covariance (`spherical`, `diag`, `tied`, `full`).

### 4. Application
- **Prédiction** : Utilisation du meilleur modèle de classification retenu à l'étape 3 pour déterminer la classe d'une nouvelle observation : `[52.1, 23.0, 6.1, 16.5]`.

## Contenu du dépôt

- `tp1.ipynb`: Le notebook Jupyter contenant tout le code Python, les analyses, les visualisations et le rapport.
- `TP1_data.csv`: Le jeu de données utilisé pour l'analyse.
- `TP1_IFT870.pdf`: L'énoncé détaillé du TP.
- `README.md`: Ce fichier, qui fournit une vue d'ensemble du projet.

## Comment utiliser ce projet

1.  Assurez-vous d'avoir un environnement Jupyter (Jupyter Notebook ou JupyterLab) installé.
2.  Installez les dépendances nécessaires :
    ```bash
    pip install pandas numpy seaborn matplotlib plotly scikit-learn
    ```
3.  Lancez Jupyter et ouvrez le fichier `tp1.ipynb`.
4.  Exécutez les cellules du notebook pour reproduire l'analyse et les résultats.