---
layout: layout/pok.njk

title: "Angular - Front-End Framework (2/2)"
authors:
  - Titouan Corne

date: 2025-01-04

tags:
  - "temps 3"
  - "vert"
  - "Dev"
  - "Web"
  - "Angular"

résumé: Ce dernier POK est consacré à l'approfondissement des connaissances du language de programmation Angular. C'est la suite de mon POK2. Je vais ainsi continuer de développer le site de cuisine Miam'Miam, j'aimerais implémenter les fonctionnalités manquantes (ajout de recette, ...), mais aussi j'aimerais écrire des tests unitaires et déployer le site sur le serveur aioli (serveur de Do-It).
---

{% prerequis %}

- Connaissances du developpement web nécessaires (html, javascript, css)

{% endprerequis %}

{% lien %}

- Doc officielle : [Angular](https://angular.dev/overview)
- Mon POK 2 : [Angular - Front-End Framework (2/2)](http://localhost:8080/promos/2024-2025/Corne-Titouan/pok/temps-2/)
- [Miam'Miam](https://github.com/TitouanCorne/ApprendreAngular/tree/main/CuisineWebSite) - projet du site de cuisine.

{% endlien %}

## Cadrage

### Objectifs principaux

1. Continuer de développer le site *Miam'Miam* pour respecter le cahier des charges [POK 2]({{ site.url }}/promos/2024-2025/Corne-Titouan/pok/temps-2/).
2. Ecrire des tests pour vérifier le bon fonctionnement du site.
3. Déployer le site sur le server aioli.

### Monitoring du projet

#### Back-log et horodateur

{% details "Sprint 1" %}

- [x] Implémenter les parties manquantes du site :
  - [x] Implémenter la partie *Mes recettes*
  - [x] Implémenter la fonctionnalité permettant de mettre une recette en favoris
  - [x] Implémenter le header pour une navigation fluide et cohérente
- [x] Tester le site :
  - [x] Revoir les tests automatiquement générés par Angular
  - [x] Ajouter des tests unitaires pour valider les différentes fonctionnalités
  - [x] Créer un jeu de données de test
  - [x] Tests pour voir si l'affichage est correct (pour la page d'accueil, pour les listes de recettes et pour les points d'information)
  - [x] Tester les endpoints (GET une recette)
  - [x] Tester les filtres
    - [x] Tester le filtre *propriétaire de la recette*
    - [x] Tester le filtre *type de recette*
    - [x] Tester le filtre *barre de recherche*
    - [x] Tester plusieurs filtres en même temps

| Date | Temps passé | Commentaire |
| -------- | -------- | -------- |
| 04/01 | 2H00 | Impélmentation fonctionnalités manquantes (mes recettes) |
| 10/01 | 2H30 | Impélmentation fonctionnalités manquantes (favoris + header)|
| 18/01 | 2H30 | Suppression anciens tests + jeu de données de test + tests d'affichage |
| 19/01 | 2H00 | Tests endpoints |
| 24/01 | 2H00 | Tests filtres |

***Temps total passé sur ce sprint :*** 11H00

{% attention %}

Faire attention à ne pas sous-estimer le temps passé à coder. C'est souvent ce que j'ai tendance à faire... Pour les nouvelles fonctionnalités implémentées lors de ce sprint, je me suis mis une limite à 4h max. Mon code fonctionne mais peut être grandement amélioré ... avec plus de temps (et de pratique !!)

{% endattention %}

{% enddetails %}

{% details "Sprint 2" %}

- [] Implémenter les parties manquantes du site :
  - [] Implémenter la fonctionnalité permettant d'ajouter une recette
  - [] Implémenter la fonctionnalité permettant de supprimer une recette
- [] Tester le site :
  - [] Tester *ajout d'une recette*
  - [] Tester *suppression d'une recette*
- [] Déployer le site sur aioli

| Date | Temps passé | Commentaire |
| -------- | -------- | -------- |
| . | . | . |

***Temps total passé sur ce sprint :*** *temps total*

{% attention %}

Possibles points d'attention

{% endattention %}

{% enddetails %}

{% faire %}

**QUOTA HORAIRE TOTAL POK 3 :** temps total cumulé avec ces deux sprints
{% endfaire %}

#### Analyse post-morterm

{% details "Sprint 1" %}

Après avoir réalisé mon MON 3.1 sur la méthodologie Test-Driven Development, j'ai été content et satisfait de voir que les connaissances acquises peuvent être facilement réutilisées. Il faut que je veille à bien documenter mon code (les tests peuvent là aussi servir), car après quelques semaines, il est difficile de se familiariser à nouveau avec du code existant.

J'ai également vu la limite de la maquette Figma (cf POK 2). Celle-ci est très pratique pour avoir une idée du rendu final. Cependant, elle ne tient pas compte de la faisabilité des fonctionnalités souhaitées. Pour illustrer cela, je peux parler du header, qui change constamment dans ma maquette (certains icônes apparaissent seulement sur des pages spécifiques). Ce header, bien que pratique sur la maquette, est affreusement compliqué, long et énervant à coder !

{% enddetails %}

{% details "Sprint 2" %}

{% enddetails %}

{% details "POK complet" %}

{% enddetails %}

## Table des matières

1. [Partie 1](#section1)
2. [Partie 2](#section2)
3. [Conclusion](#section3)

## Partie 1 <a id="section1"></a>

suite à venir (en cours de rédaction)

## Partie 2 <a id="section2"></a>

## Conclusion <a id="section3"></a>
