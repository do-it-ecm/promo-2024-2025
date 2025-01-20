---
layout: layout/mon.njk

title: "Faire du software qui dure: Documentation"
authors:
  - Loïck Goupil-Hallay

date: 2025-01-20

temps: 3

tags:
  - 'dev'
  - 'documentation'

résumé: "Comment documenter son logiciel / son infrastructure / sa plateforme pour qu'il soit maintenable et évolutif."
---

<head>
  <link rel="icon" href="https://github.com/BoxBoxJason/resume/blob/d07f37a66e2a583832533a10a9a4bf73b020be6f/src/assets/avatar.png?raw=true" type="image/x-icon">
</head>

{% sommaire %}
[[toc]]
{% endsommaire %}

{% lien "**Liens utiles**" %}
- [Faire du software qui dure: Philosophie](../temps-3.2)
{% endlien %}

## Introduction

C'est bien beau de faire du code qui marche, mais quand on est un ingénieur / une entreprise sérieux, cela ne suffit pas.\
Il faut avant tout que le code soit **maintenable** et **évolutif**.\
Il faut que la production soit **documentée** pour permettre au client de l'utiliser correctement. Mais aussi pour permettre à d'autres développeurs de **comprendre le code** / l'infastructure / la plateforme et de le modifier sans passer 4 semaines à comprendre comment il fonctionne.\
Il faut notamment que **d'autres personnes puissent administrer** tout cela sans avoir besoin de vous appeler à chaque fois.

C'est un problème qui peut paraître anodin pour des novices qui n'ont travaillé que sur des petits projets personnels. Cependant c'est une tare qui coûte **EXCESSIVEMENT cher** en entreprise. *C'est aussi une des principales raisons pour lesquelles les ingénieurs en informatique sont si bien payés.*

Pour illustrer mon propos, nous allons utiliser l'exemple concret (*tout à fait au hasard*) de la mise à jour 3.0.0 de la plateforme Do-It.\
La mise à jour à apporté un nombre conséquent de nouveautés et de changements qui se doivent d'être documentés pour que les utilisateurs puissent en profiter pleinement.

## Théorie

## Cas pratique
