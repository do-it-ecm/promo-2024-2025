---
layout: layout/pok.njk

title: "Recommndation de films avec Pyspark"
authors:
  - Baptiste Audouin

date: 2025-01-23

temps: 3
tags:

résumé: Ce projet a pour objectif de développer un système de recommandation de films en utilisant le modèle de machine learning ALS (Alternating Least Squares) de PySpark, librairie d'analyse de données et de machine learning.
---

{% prerequis %}

- Bases en python

{% endprerequis %}
{% lien %}

- [Théorie du  modèle ALS sur le site flink](https://nightlies.apache.org/flink/flink-docs-release-1.4/dev/libs/ml/als.html)
- [Dataset MovieLens sur kaggle](https://www.kaggle.com/datasets/grouplens/movielens-20m-dataset?select=rating.csv)
- [Documentation PySpark](https://spark.apache.org/docs/latest/api/python/index.html)

{% endlien %}

Au cours de mon cursus j'ai déjà eu l'occasion de travailler sur des modèles de Machine Learning comme kNN (k-Nearest Neighbors) ou Matrix Factorization (SVD - Singular Value Decomposition) de la librairie *scikit-learn*. Dans ce POK je voudrais travailler avec PySpark qui est une bibliothèque Python qui permet de traiter de grandes quantités de données rapidement en utilisant Apache Spark. Très utilisé en data science, il aide à analyser et manipuler des données massives de manière efficace. Je souhaite appliquer le modèle ALS (Alternating Least Squares) à un dataset de notation de films afin de faire un systèmede recommandation.

## Cadrage

### Objectifs principaux

1. Comprendre la théorie du modèle ALS.
2. Préparer les données
3. Implémenter le modèle de recommandation
4. Évaluer les performances

### Sprints

#### Sprint 1

- [ ] Documentation sur le théorie du modèle ALS (1h)
- [ ] Recherche et sélection du dataset (ex. MovieLens) (1h)
- [ ] Préparation de l'environnement PySpark (1h)
- [ ] Exploration initiale des données (analyse des colonnes et visualisation) (1h)
- [ ] Nettoyage et transformation des données (gestion des valeurs manquantes, typage) (2h)
- [ ] Création de matrices utilisateurs-films et exploration des modèles de base (2h)

#### Sprint 2

- [ ] Implémentation du modèle de recommandation avec ALS (Alternating Least Squares) (4h)
- [ ] Optimisation des hyperparamètres du modèle (3h)
- [ ] Évaluation des performances (précision, rappel, RMSE) (2h)
- [ ] Génération de recommandations pour les utilisateurs (2h)
- [ ] Documentation finale et présentation des résultats (1h)


### Horodatage

Toutes les séances et le nombre d'heure que l'on y a passé.

| Date | Heures passées | Indications |
| -------- | -------- |-------- |
| Jeudi 23/01  | 2H  | Cadrage et documentation sur le modèle ALS |

## Contenu


### Premier Sprint

#### Le modèle ALS (Alternating Least Squares) 

Voici une explication un peu plus détaillée :  

Le modèle **ALS (Alternating Least Squares)** est une méthode de factorisation matricielle utilisée pour les systèmes de recommandation. Il vise à décomposer une matrice \( R \) représentant les interactions entre utilisateurs et éléments (comme les notes attribuées à des films dans ce POK) en deux matrices plus petites :  
- \( U \) : une matrice \( n \times k \) représentant les préférences des utilisateurs.  
- \( M \) : une matrice \( m \times k \) représentant les caractéristiques des éléments (les films ici).  

Ces deux matrices sont calculées de manière à approximer \( R \) :  
\[
R \approx U \cdot M^T
\]  

L'objectif est de minimiser l'erreur entre les valeurs prédites \( U_u^T M_i \) (produit des vecteurs utilisateur et élément) et les notes réelles \( R_{ui} \), tout en évitant le surapprentissage grâce à une régularisation :  
\[
\min_{U, M} \sum_{(u, i) \in R} \left( R_{ui} - U_u^T M_i \right)^2 + \lambda \left( \|U_u\|^2 + \|M_i\|^2 \right)
\]  
où :  
- \( \lambda \) est un paramètre de régularisation pour pénaliser les valeurs extrêmes dans \( U \) et \( M \).  
- \( \|U_u\|^2 \) et \( \|M_i\|^2 \) sont des normes qui contrôlent la taille des vecteurs.  

### Fonctionnement de l'optimisation  
ALS alterne entre :  
1. **Fixer \( M \)** et résoudre \( U \).  
2. **Fixer \( U \)** et résoudre \( M \).  

Ce processus est répété jusqu'à ce que l'erreur converge vers une valeur minimale.  

### Points forts  
- **Gestion des données creuses** : ALS est bien adapté aux matrices où la majorité des interactions sont inconnues.  
- **Parallélisation** : Grâce à son alternance entre \( U \) et \( M \), ALS peut être distribué efficacement, par exemple avec Spark.  


### Second Sprint
