---
layout: layout/mon.njk

title: "Firebase"
authors:
  - Victor Pawlaczyk

date: 2025-02-01
temps: 3
tags: 
- Vert
- Firebase

résumé: "Découverte de Firebase"
---

{% lien %}

[MON de Guillaume sur Firebase](https://francoisbrucker.github.io/do-it/promos/2024-2025/Oliana-Guillaume/mon/temps-2.1/)

{% endlien %}

## Qu'est-ce que firebase ?

Le [MON de Guillaume sur Firebase](https://francoisbrucker.github.io/do-it/promos/2024-2025/Oliana-Guillaume/mon/temps-2.1/) est très bien construit et m'a permis de comprendre le champs des possibles offert par firebase. Il serait inutile de le paraphraser ici.

Parmi toutes les fonctionnalités de Firebase, il y a entre autres la Firebase Realtime Database et le cloud Firestore. Au cours de mes recherches, j'ai très souvent lu que ces modules étaient des bases de données NoSQL. Pour les incultes comme moi, une BDD NoSQL ("Not Only SQL") est non relationnelle, contrairement aux bases plus "classiques". Ainsi, leur schéma est beaucoup plus libre. Cela permet principalement de stocker et de travailler plus facilement de la bigdata qu'avec les BDD relationnelles. La Firebase Realtime Database exploite le NoSQL pour permettre à des applications web de fonctionner en temps réel, c'est-à-dire que les données, dès qu'elles sont modifiées, se mettent instantanément à jour sur l'application web.

## Un peu de manipulation

J'ai suivi une partie du cours sur Firebase proposé sur [Openclassrooms](https://openclassrooms.com/fr/courses/4872916-creez-un-backend-scalable-et-performant-sur-firebase/4872923-titre-de-votre-premier-chapitre-222) afin d'effectuer et de comprendre quelques manipulations et applications. Ainsi, j'ai pu suivre étape par étape l'intégration de Firebase dans une application androïd et l'utilisation du système d'authentification proposé par Firebase. Cela m'a permis de mieux cerner comment fonctionne le système d'authentification utilisé dans notre application mobile pour notre projet 3A. Dans ce cours, je me suis très vite retrouvé bloqué par mes lacunes en html et Javascript. J'ai vraiment aucune connaissance sur ces sujets donc pour manipuler et faire les exemples en parallèle des étapes d'openclassrooms c'était mission impossible à improviser sur l'unique temps de travail de ce MON. Pour autant, j'ai un peu avancé dans la lecture du cours d'openclassrooms et grâce à celà j'ai pu comprendre certains choix d'organisation des données que l'on a fait pour le projet 3A et pour lesquels je n'avais à ce moment là pas suffisamment de connaissances sur le sujet pour pouvoir vraiment me prononcer sur ces choix.

Pour essayer d'approfondir, j'ai manipulé la realtime database directement dans la console firebase depuis mon navigateur internet. J'ai pu rentrer quelques données à titre d'exemple. On peut très facilement créer une petite arborescence avec quelques données de manière "low code" via cette interface. Cette même interface permet d'un autre côté d'importer des jeux de données tout prêts directement en format JSON et de les visualiser très rapidement de manière plus graphique avec leur arborescence. Malheureusement je n'ai pas pu réellement éprouver l'avantage principale de realtime database, qui est la mise à jour instantanée des données. Cela permet par exemple de gérer les données d'une application de messagerie ou de chat en temps réel.

## Conclusion

J'ai maintenant plus conscience de ce en quoi consiste Firebase, que l'on utilise pour l'application de notre projet 3A. J'ai pu découvrir les différentes fonctionnalités proposées et les applications courantes qui en sont faites. Malheureusement, pour pouvoir vraiment utiliser et exploiter les différents modules de firebase, il faut avoir en parallèle un projet codé dans lequel on peut intégrer firebase et solliciter les différentes fonctionnalités. N'ayant aucune connaissance en HTML, Javascript ou quelconque autre langage qui aurait pu me permettre de monter des petits projets simples pour tester de manière indépendantes certaines fonctionnalités, j'ai dû m'arrêter à cette étape théorique assez frustrante dans le cadre de ce MON. Pour autant, comme me l'a appris Do_It pendant ma 3A, il est important de prendre du temps dans son quotidien pour se former, s'intéresser à de nouvelles choses et ouvrir ses horizons, afin d'étendre continuellement notre capacité à suivre des problématiques toujours plus variées et/ou transverses. Ces lacunes en html et javascript étant maintenant identifiées, et ayant des exemples plus concrets en tête de ce que ces langages permettent, j'aurai certainement l'occasion de me renseigner à leur sujet pour pouvoir bricoler un peu avec tous ces outils.