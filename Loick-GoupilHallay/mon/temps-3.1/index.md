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
- [10 best practices for writing documentation](https://www.geeksforgeeks.org/best-practices-for-writing-documentation/)
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

En ingénierie logicielle, la documentation sert à **décrire** le code, l'infrastructure ou la plateforme.\
Elle permet de **comprendre** comment cela fonctionne, comment l'utiliser, comment le modifier, comment le déployer, ou tout autre information **nécessaire**.

### Cible

La première étape pour bien documenter est de **déterminer la cible**.\
Il est important de savoir qui va lire la documentation pour adapter le contenu et le niveau de détail.\
Un *utilisateur* n'a pas besoin de la même information qu'un *développeur* ou un *administrateur système*.\
Il est donc important de **déterminer les différentes cibles** et de **créer une documentation pour chacune d'entre elles**.

Il y a évidemment la majorité des informations qui sont communes à toutes les cibles, cependant chaque cible a des **besoins spécifiques** qui doivent être pris en compte.

#### Développeur

En entreprise, le développeur est la première cible de la documentation. Ce sont eux qui vont **maintenir** et **faire évoluer** le code. Ils doivent donc parfaitement comprendre son fonctionnement sans avoir besoin de vous appeler à chaque fois.
Il est donc important de **fournir une documentation technique** qui explique comment le code fonctionne, comment il est structuré, comment il est testé, comment il est déployé,... Cette documentation doit être faite à la fois dans le code (commentaires, docstrings, ...) et à l'extérieur du code (wiki, README, ...).

Vous pouvez considérer que la documentation technique est une sorte de **manuel d'utilisation** pour les développeurs.\
Par conséquent, vous pouvez utiliser des termes techniques et des concepts avancés qui ne sont pas forcément compréhensibles par un utilisateur lambda.

Les diagrammes UML, les schémas, les exemples de code, les explications détaillées, les références, les liens vers des ressources externes,... sont des outils très utiles pour aider le développeur à comprendre le code.

#### Utilisateur

L'utilisateur est la personne qui va **utiliser** le logiciel / l'infrastructure / la plateforme.\
Il n'a pas besoin de savoir comment cela fonctionne, il a juste besoin de savoir **comment l'utiliser**.\
Il est donc important de **fournir une documentation simple et claire** qui explique comment utiliser le produit.

Il faut impérativement garder en tête que l'utilisateur n'a pas les mêmes connaissances que vous.\
Il est donc important de **simplifier au maximum** les explications et de **fournir des exemples** pour illustrer vos propos.\
Il faut dans l'idéal écrire la documentation comme si vous expliquiez à un enfant de 10 ans, sans aucune compétence technique ni capacité de reflexion. Ainsi, vous êtes sûr que tout le monde pourra comprendre.

Les guides d'utilisation, les tutoriels, les FAQ, les vidéos, les infographies, les schémas, les captures d'écran, les exemples de code,... sont des outils très utiles pour aider l'utilisateur à comprendre comment utiliser le produit.

### Stratégie

Votre documentation doit suivre une stratégie établie pour être efficace.\
Vous devez donc **définir un objectif** pour éviter de vous éparpiller et de perdre du temps.

Il existe 3 écoles pour documenter son code:

#### Document after you code

Vous écrivez votre code, puis vous documentez.\
C'est malheureusement la méthode la plus **courante**, mais aussi la plus risquée.\
En effet, il est très facile d'oublier de documenter une partie du code, ou de ne pas documenter correctement.\
De plus, il est très difficile de se rappeler de tous les détails du code une fois que vous avez fini de l'écrire.\
C'est une méthode qui peut être très chronophage et qui peut entraîner des erreurs si elle n'est pas bien maîtrisée.

#### Document before you code

Vous écrivez la documentation avant de coder.\
En écrivant la documentation avant de coder, vous êtes obligé de **réfléchir** à ce que vous allez coder, à comment vous allez le coder, à comment vous allez le tester,...\
Cela vous permet de **clarifier vos idées** et de **planifier** votre code avant de le coder.\
Cela vous permet aussi de **définir les interfaces** et les **contrats** entre les différentes parties de votre code.\
C'est une méthode qui peut vous faire gagner beaucoup de temps et qui peut vous éviter de nombreux problèmes.

*Pour rester agile, essayez de documenter les grandes lignes avant de coder, puis de documenter les détails au fur et à mesure que vous codez.*

#### Document as you code

Vous écrivez la documentation en même temps que vous codez.\
C'est une méthode **agile** qui combine les avantages des deux méthodes précédentes.\
En écrivant la documentation en même temps que vous codez, vous êtes sûr de ne rien oublier et de ne pas avoir à y revenir plus tard.\
C'est une méthode qui peut vous faire gagner beaucoup de temps et qui peut vous éviter de nombreux problèmes.

*Cela n'empêche pas de planifier et de réfléchir à ce que vous allez coder avant de le coder.*

### Contenu

La documentation doit suivre des **règles** et être **structurée**. De plus certaines informations sont **indispensables** pour que la documentation soit **efficace**.

#### Simplicité

L'important est d'être **simple** et **claire**.\
Elle doit être **facile à lire** et **facile à comprendre**.\
Il est important d'utiliser des **exemples** et des **schémas** pour **illustrer** vos propos.

#### Complétude

La documentation doit être **complète**.\
Cela ne veut pas dire qu'elle doit être **longue**, mais qu'elle doit **contenir toutes les informations nécessaires**.\
Il est important de **préciser** les choses et de **ne pas laisser de place à l'interprétation**.

#### Navigabilité

Pensez votre documentation pour qu'elle soit **facile à naviguer**.\
Les parties importantes doivent être **facilement accessibles** et mises en **évidence**.

#### Format et style

Le style et le format de la documentation doivent être **uniformes**.\
Cela permet de **faciliter la lecture** et de **rendre la documentation plus professionnelle**.

### Participants

Il faut impérativement éviter qu'une seule personne subisse la responsabilité de la documentation.\
Cela pose de multiples problèmes tels que:
- Concentration de la connaissance / Risque de perte de connaissance
- Ouverture à la critique / Risque de conflit
- Risque de perte de temps
- Risque de perte de qualité
- Risque d'oublis / de fautes

Pour cela, il faut **impliquer tout le monde** dans la documentation.\
Chaque personne doit **documenter son travail** et **partager ses connaissances** avec les autres.

Il faut aussi bien sûr **vérifier** la documentation en passant par une étape de **relecture**.\
Cela permet de **corriger les erreurs** et de s'assurer de la **qualité**  et de la **complétude** de la documentation.

## Cas pratique

Pour illustrer mes propos, je vous invite à consulter la documentation de la mise à jour 3.0.0 de la plateforme Do-It
(*j'espère qu'elle est toujours en place au moment où vous lisez ces lignes*).

Il y a des guides avec exemples **orientée utilisateur** qui expliquent [comment utiliser toutes les fonctionnalités de la plateforme]({{ site.url }}/contribuer/).

Il y a aussi une documentation **orientée développeur** disponible sur [le dépôt GitHub de la plateforme]({{ site.source }}) (les fichiers README et CONTRIBUTING)

### Auto Evaluation

Selon les critères décrits ci-dessus, voici une auto-évaluation de la documentation de la mise à jour 3.0.0 de la plateforme Do-It.

|Critère| Cible | Stratégie | Simplicité | Complétude | Navigabilité | Format & Style | Participants |
|---| --- | --- | --- | --- | --- | --- | --- |
|Documentation Utilisateur| ✅ ciblé | ❌ après | ✅ simple | ✅ complète | ✅ navigable | ✅ uniforme | ❌ 1 auteur |
|Documentation Développeur| ✅ ciblé | ✅ avant + edit | ✅ simple | ❌ complète | ✅ navigable | ✅ uniforme | ❌ 1 auteur |
