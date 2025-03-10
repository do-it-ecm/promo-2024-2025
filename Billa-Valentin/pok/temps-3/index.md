---
layout: layout/pok.njk

title: "Optimization"
authors:
  - Valentin Billa

# date: 2024-18-12

temps: 3

tags:
  - 'vert'
  - 'avancé'
  - 'optimisation'
  - 'benchmarking'
  - 'rust'

résumé: Tentative d'optimisation d'un algorithme de génération de labyrinthe grâce à des structures de données appropriées en Rust. 
---

{% sommaire %}
${toc}
{% endsommaire %}

{% prerequis %}
- Bases de Rust
- Connaissances en structures de données
{% endprerequis %}

## Objectifs

{% attention %}
Cet article est en cours d'écriture, le planning et le suivi sont là, mais tout n'est pas terminé.
{% endattention %}

Je souhaite approfondir mes connaissances en rust et apprendre à mieux m'y prendre pour optimiser des algorithmes.
L'objectif est de créer un générateur de labyrinthe pour ensuite utiliser ce projet comme prétexte pour en 
apprendre plus sur les techniques d'optimisation ainsi que les structures de données plus niches en Rust.

Aussi, j'ai aussi utilisé les connaissances acquises lors de ce POK pour réécrire un algorithme initialement
rédigé en Python vers Rust, pour générer des mosaïques à la vitesse de la lumière (ou presque) pour notre projet 3A.
{% lienInterne "/promos/2024-2025/_projets/mosaiques/#frontend" %}

{% note "**Mauvaises pratiques**" %}
Ce sera abordé dans la partie [Optimisation](#Optimisation), mais il faut savoir que généralement optimiser juste
pour optimiser est généralement **mauvaise idée**. Ce POK n'étant pas lié à project concret, c'est sans
trop de vergogne que je vais me déroger aux bonnes pratiques à des fins d'expérimentation !
{% endnote %}

### Rudiments de Rust
Plusieurs POK&MONs ont déjà été réalisés sur les rudiments de Rust, je ne m'y attarderais donc pas.
Entre autres, je peux recommander la lecture des deux suivants (non pas que je ne
recommande pas les autres, je ne les ai simplement pas tous lus).

{% lienInterne "/promos/2023-2024/Diouf-Asssane/mon/Rust/" %}
{% lienInterne "/promos/2023-2024/Victor-Ory/pok/temps-1/" %}

## Sprint 1
### Planning Prévisionnel
#### 1.1 Mise en place et tests
- [X] Création d'une interface labyrinthe qu'implémenteront mes structures de données.
- [X] Création de tests pour les implémentations de cette interface.

#### 1.2 Implémentation de l'interface
- [X] Implémentation de l'interface de façon naïve.
- [X] Création d'une fonction permettant de visualiser un labyrinthe.
- [] Rédaction d'un algorithme de génération utilisant l'interface.

{% info %}
J'ai dû créer l'implémentation de l'interface naïve avant les tests, pour pouvoir tester les tests...
Ce sera abordé plus tard, mais les tests m'ont donné par mal de fil à retordre.
{% endinfo %}

### Optimisation

Au cours de mes recherches, je suis tombé sur deux citations qui me semblent pertinentes à partager :

[Donald Knuth](https://en.wikipedia.org/wiki/Donald_Knuth)
> Premature optimization is the root of all evil.

[Michael A. Jackson](https://en.wikipedia.org/wiki/Michael_A._Jackson_(computer_scientist)) \
*À ne pas confondre avec Michael Jackson tout court dont l'opinion en informatique est probablement beaucoup moins pertinente.* &#128378;
> Rules of Optimization: \
> • Rule 1: Don't do it. \
> • Rule 2 (for experts only): Don't do it yet.

<!-- TODO: Utiliser cette source https://www.cs.princeton.edu/courses/archive/spring19/cos217/lectures/11_Performance.pdf -->

### Interface
### Tests
### Structure naïve
### Visualisation

### Horodatage

| Date              | Heures passées | Indications                         |
|-------------------|----------------|-------------------------------------|
| 16 Janvier (Jeu.) | 2H             | Interface & Tests                   |
| 19 Janvier (Dim.) | 5H             | Tests                               |
| 25 Janvier (Sam.) | 3H             | Visualisation & Début de génération |
| **Total**         | **10H**        |                                     |

### Rétro

## Sprint 2
### Planning Prévisionnel
#### 1.2
- [X] Rédaction de l'algorithme de génération.

#### 2.1 Benchmarking
- [X] Créer des fonctions permettant de tester à sur de nombreux seeds connus en avance.

#### 2.2 Optimization
- [X] Identifier les bottle necks avec un flame graph.
- [X] Améliorer l'algorithme de génération.
- [X] Proposer d'autres structures de données.

### Algorithme de génération
### Benchmarking
### Compilation Optimisée
### Flame Graph
### Amélioration de l'algorithme
### Impact théorique de structures de données adaptées
### Impact pratique
### Structures testées

### Horodatage

| Date           | Heures passées | Indications                                       |
|----------------|----------------|---------------------------------------------------|
| 03 Mars (Lun.) | 2h             | Algorithme de génération & d'autres tests...      |
| 08 Mars (Sam.) | 4h             | [^1]                                              |
| 09 Mars (Dim.) | 4h             | Bidouilles avec différentes structures de données |
| **Total**      | **10H**        |                                                   |

[^1] Fonction de benchmarking, ajout de seeding dans l'algorithme de génération, identification de bottle
necks et premières optimisations.

### Rétro
