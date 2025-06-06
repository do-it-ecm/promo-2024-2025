---
layout: layout/mon.njk

title: "Faire du software qui dure: Philosophie"
authors:
  - Loïck Goupil-Hallay

date: 2025-02-15

temps: 3

tags:
  - 'dev'
  - 'philosophie'

description: "Comment penser son logiciel / son infrastructure / sa plateforme pour qu'il soit maintenable et évolutif."
---

<head>
  <link rel="icon" href="https://github.com/BoxBoxJason/resume/blob/d07f37a66e2a583832533a10a9a4bf73b020be6f/src/assets/avatar.png?raw=true" type="image/x-icon">
</head>

{% sommaire %}
[[toc]]
{% endsommaire %}

{% lien "**Liens utiles**" %}
- [Faire du software qui dure: Documentation](../temps-3.1)
{% endlien %}

## Introduction

C'est bien beau de faire du code qui marche, mais quand on est un ingénieur / une entreprise sérieux, cela ne suffit pas.\
Il faut avant tout que le code soit **maintenable**, **évolutif**, **déployable**, **sécurisé**, **performant**, **scalable**, **monitorable**, **testable**, **durable** et tous pleins d'autres adjectifs en -able.\
Le software de production / de grande échelle doit être un véritable travail d'orfèvre.\
Dans ce MON nous allons voir quelques bonnes pratiques et philosophies à adopter pour que votre software puisse s'inscrire dans le temps
