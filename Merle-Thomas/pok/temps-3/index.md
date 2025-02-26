---
layout: layout/pok.njk

title: "POK 3 - Computer Vision - Lane Detection Pipeline"
authors:
  - Thomas Merle

date: 2025-02-25

tags:
  - 'temps 3'
  - 'Computer Vision'
  - 'Automative Technology'
  - 'Notebook'
  - 'Python'
  - 'OpenCV'
  - 'bibiothèques'
  

résumé: "Détection de lignes de voie sur Images et Vidéos : application à l'automobile"
---
{% prerequis %}
**Niveau :** Technique
**Pré-requis:**

- Connaissance de Python et des bibliothèques OpenCV, NumPy et Matplotlib.
- Notions de base en traitement d'image (filtres, détection de contours, seuillage).
- Compréhension des concepts de segmentation et de détection de formes.
{% endprerequis %}

{% lien %}
['Repo Github'](https://github.com/ThomasMerle25/Lane_Detection_Pipeline)
{% endlien %}

Quelques phrases permettant de connaître, sans jargon ni blabla, le contenu de ce POK. On oubliera pas de donner :

- le niveau et les prérequis nécessaires en utilisant la balise [`prerequis`](/cs/contribuer-au-site/#prerequis)
- les autres POK & MON en rapport en utilisant la balise [`lien`](/cs/contribuer-au-site/#lien)

# POK3 - Computer Vision - Lane Detection Pipeline

---
## Table des matières<a name="table-des-matières"></a>

- [POK3 - Computer Vision - Lane Detection Pipeline](#pok3---computer-vision---lane-detection-pipeline)
  - [Table des matières](#table-des-matières)
  - [Objectifs principaux](#objectifs-principaux)
  - [Rappels théoriques et justification des choix techniques](#rappels-théoriques-et-justification-des-choix-techniques)
  - [Sprints](#sprints)
    - [Sprint 1 : Exploration des données](#sprint-1--exploration-des-données)
    - [Sprint 2 : Mise en place des outils et bibliothèques](#sprint-2--mise-en-place-des-outils-et-bibliothèques)
    - [Sprint 3 : Développement des fonctions de traitement d'image](#sprint-3--développement-des-fonctions-de-traitement-dimage)
    - [Sprint 4 : Construction du pipeline de traitement d'image](#sprint-4--construction-du-pipeline-de-traitement-dimage)
    - [Sprint 5 : Application aux images et vidéos](#sprint-5--application-aux-images-et-vidéos)
    - [Retour d’expérience](#retour-dexpérience)
    - [Conclusion](#conclusion)
  - [Horodateur](#horodateur)

---

Ce travail vise à développer un pipeline de Computer Vision capable de détecter les lignes de voie sur des images et des vidéos. Ce projet permet de mettre en pratique de nouveaux concepts de Machine Learning que nous ne voyons pas à Centrale, en s'appuyant sur la bibliothèque OpenCV de Python. Les données utilisées proviennent du programme "Self Driving Car Engineer Nanodegree" d'Udacity. J'ai créer un notebook Python développé sur Jupyter via l'environnement Anaconda.

---

## Objectifs principaux

1. Concevoir un pipeline de traitement d'image capable de détecter les lignes de voie.

2. Appliquer des techniques de traitement d'image et d'analyse de contours.

3. Automatiser l'application du pipeline sur des images et des vidéos.

4. Expérimenter les fonctions d'OpenCV pour la vision par ordinateur.

## Rappels théoriques et justification des choix techniques

Pour les personnes n'ayant pas de connaissance préalable des techniques utilisées, voici quelques rappels essentiels ainsi qu'une explication des choix technologiques :

- **Traitement d'image** : Ensemble des techniques permettant d'améliorer, modifier ou extraire des informations d'une image. La vision par ordinateur repose fortement sur ce domaine pour analyser et comprendre les images.

- **Filtrage et réduction du bruit** : Un filtre gaussien est appliqué pour lisser l’image et éliminer les variations de pixels parasites dues au bruit. Ce choix est pertinent car il permet de préserver les contours tout en supprimant les informations inutiles.

- **Conversion en niveaux de gris** : Transformer une image couleur en niveaux de gris simplifie son traitement tout en conservant les informations essentielles sur les contrastes et les contours.

- **Détection de contours avec l’algorithme de Canny** : L'algorithme de Canny est utilisé pour détecter les bords des objets présents dans l’image. Ce choix est motivé par sa robustesse : il permet d’obtenir des contours nets et exploitables tout en supprimant les artefacts liés au bruit.

- **Définition d'une région d'intérêt (ROI)** : Pour se concentrer uniquement sur la route et les lignes de voie, on applique un masquage qui exclut les zones non pertinentes de l’image. Cela réduit la quantité d’informations à traiter et améliore la précision de la détection.

- **Transformée de Hough pour la détection des lignes** : Cet algorithme permet de détecter des formes géométriques dans une image. Il est idéal pour identifier les lignes de marquage routier, car il recherche des alignements de pixels formant des lignes droites.

D'autres méthodes comme la segmentation sémantique par réseaux de neurones auraient pu être utilisées, mais elles nécessitent un entraînement complexe et des ressources de calcul importantes.

- **Superposition des résultats sur l'image originale** : Une fois les lignes détectées, elles sont dessinées sur l’image initiale pour obtenir un affichage intuitif et compréhensible.

---

## Sprints

### Sprint 1 : Exploration des données

- **Tâches** :
  - [x] Chargement des images et vidéos fournies par Udacity.
  - [x] Visualisation des données pour comprendre les caractéristiques des lignes de voie.
  - [x]Analyse des difficultés potentielles : variations d'éclairage, différents types de routes, présence de bruit.

### Sprint 2 : Mise en place des outils et bibliothèques

- **Tâches** :
  - [x] Installation et importation des bibliothèques Python nécessaires : OpenCV, NumPy, Matplotlib.
  - [x] Configuration de l'environnement de travail et vérification du bon chargement des données.

### Sprint 3 : Développement des fonctions de traitement d'image

- **Tâches** :
  - [x] Implémentation d'une fonction de conversion en niveaux de gris pour simplifier l'analyse.
  - [x] Développement d'un filtre gaussien pour réduire le bruit de l’image.
  - [x] Mise en place de la détection des contours avec l’algorithme de Canny.
  - [x] Définition d’une région d’intérêt (ROI) pour se concentrer sur la zone utile.

### Sprint 4 : Construction du pipeline de traitement d'image

- **Tâches** :
  - [x] Intégration des différentes étapes (filtrage, détection de contours, ROI) dans une fonction unique
  - [x] Implémentation de la transformée de Hough pour identifier les lignes de voie.
  - [x] Superposition des lignes détectées sur l’image d’origine.
  - [x] Vérification du bon fonctionnement du pipeline sur des images tests.

### Sprint 5 : Application aux images et vidéos

- **Tâches** :
  - [x] Application du pipeline à une série d'images pour vérifier la robustesse du modèle.
  - [x] Extension du pipeline aux vidéos : lecture frame par frame et traitement en temps réel.
  - [x] Ajustement des paramètres de détection (seuils de Canny, paramètres de Hough) pour améliorer la robustesse et la précision.
  - [x] Comparaison des résultats obtenus sur différentes conditions de routes.

---

### Retour d’expérience

1. **Ce que j’ai appris:**

- Compréhension approfondie des étapes du traitement d'image appliquées à la détection de lignes.
- Importance du réglage des hyperparamètres pour obtenir des résultats optimaux.
- Adaptation du pipeline aux variations de conditions de route (lumière, bruit, obstacles).
- Manipulation avancée des fonctions OpenCV pour la vision par ordinateur.

2. **Difficultés rencontrées:**

- Ajustement des seuils de Canny et des paramètres de la transformée de Hough pour obtenir une détection fiable sans faux positifs.
- Gestion des conditions de lumière variables, qui impactent la qualité de la détection des contours.
- Détection de lignes interrompues ou discontinues dues à l’usure des marquages au sol.
- Optimisation du pipeline pour garantir un bon compromis entre performance et temps de calcul sur des vidéos.

### Conclusion

Ce projet met en application plusieurs techniques de Computer Vision pour résoudre un problème concret de détection de lignes de voie. L’approche basée sur OpenCV permet d’obtenir un résultat efficace tout en minimisant la complexité computationnelle. D'autres méthodes, comme l'apprentissage profond, auraient pu être envisagées mais nécessitent des ressources et une annotation de données plus importantes. Ce pipeline peut être étendu et optimisé pour des applications avancées, notamment en conduite autonome.

---

## Horodateur

Toutes les séances et le nombre d'heure que l'on y a passé.

| Date       | Heures passées | Indications                                    |
|------------|----------------|------------------------------------------------|
| 16/01 |       4H    | Définition du sujet et des objectifs : Documentation sur les techniques de Computer Vision |
| 17/01 |       2H    | Exploration des données : Chargement et analyse des images/vidéos. |
| 20/01 |       2H    | Mise en place des outils : Installation et test des bibliothèques. |
| 29/01 - 14/02 |     6H      | Développement des fonctions de traitement d'image : Implémentation et tests des différentes étapes (conversion, filtrage, Canny, ROI). |
| 24/02 |      4H     | Construction du pipeline : Intégration des étapes et ajustement des paramètres. |
| 25/02 |     4H      | Application aux images et vidéos : Tests et ajustements sur plusieurs conditions. |
