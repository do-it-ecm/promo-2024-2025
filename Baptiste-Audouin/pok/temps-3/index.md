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

Le modèle **ALS (Alternating Least Squares)** est utilisé pour les systèmes de recommandation. Il cherche à décomposer une matrice \\( R \\), qui représente les interactions entre utilisateurs et éléments (comme les notes attribuées à des films pour ce POK), en deux matrices plus petites :

- \\( U \\) : matrice des préférences des utilisateurs.
- \\( M \\) : matrice des caractéristiques des éléments (comme les films).

L'approximation se fait avec la relation suivante :  
$$
R \\approx U \\cdot M^T
$$

L'objectif est de minimiser l'erreur entre les valeurs prédites \\( U_u^T \\cdot M_i \\) et les notes réelles \\( R_{ui} \\)
tout en ajoutant une régularisation pour éviter le surapprentissage. La fonction d'optimisation est :  

$$
\\min_{U, M} \\sum_{(u, i) \\in R} \\left( R_{ui} - U_u^T M_i \\right)^2 + \\lambda \\left( ||U_u||^2 + ||M_i||^2 \\right)
$$

**Où :**

- \\(lambda\\) : paramètre de régularisation pour limiter les valeurs extrêmes dans \\( U \\) et \\( M \\).
- \\( ||U_u||^2 \\) et \\( ||M_i||^2 \\) : normes des vecteurs utilisateur et élément.


#### Fonctionnement d'ALS

1. Fixer la matrice \\( M \\) et calculer \\( U \\).
2. Fixer la matrice \( U \) et calculer \( M \).

Le processus alterne entre ces deux étapes jusqu'à ce que l'erreur soit suffisamment basse.

#### Exemple simple

Supposons une matrice \\( R \\) comme celle-ci (notes données par des utilisateurs) :  

| Utilisateur / Film | Film 1 | Film 2 | Film 3 |  
|---------------------|--------|--------|--------|  
| Utilisateur 1       | 5      | ?      | 3      |  
| Utilisateur 2       | ?      | 4      | ?      |  
| Utilisateur 3       | 1      | ?      | 2      |  

Le modèle utilise \\( U \) et \\( M \\) pour prédire les notes manquantes (notées "?"). En ajustant itérativement \\( U \\) et \\( M \\), ALS minimise l'erreur entre les prédictions et les notes réelles.

#### Choix du Dataset

Pour ce projet , j'ai choisi le dataset **MovieLens** disponible sur Kaggle, un des datasets les plus populaires pour les systèmes de recommandation. Ce dataset contient des millions de notes attribuées à des films par des utilisateurs. Il inclut plusieurs fichiers, dont les principaux sont :

- **movies.csv** : Contient les informations sur les films, notamment l'ID du film, le titre et les genres associés.
- **ratings.csv** : Contient les évaluations des utilisateurs pour les films, avec l'ID de l'utilisateur, l'ID du film, la note attribuée et la date de l'évaluation.
- **tags.csv** : Contient des informations sur les tags associés aux films, qui peuvent être utiles pour l'analyse des préférences.


### Second Sprint
