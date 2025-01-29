---
layout: layout/mon.njk

title: "Projet Numérologie pour notions de back-end"
authors:
  - Lola Perdrix

date: 1971-03-01
tags: 
  - "temps 3"
  - "vert"
  - "back"

résumé: "Ce MON vise à découvrir les notions de back-end, la création de serveurs web, et la gestion de base de données avec les outils fournis sur le cours de M.Brucker"
---

{% prerequis %}
Notions de javascript
{% endprerequis %}
{% lien %}

- [Doc javascript](https://developer.mozilla.org/en-US/docs/Web/JavaScript)
- [Cours web](https://francoisbrucker.github.io/cours_informatique/cours/web/)
- [Projet Numérologie](https://francoisbrucker.github.io/cours_informatique/cours/web/projet-num%C3%A9rologie/)

{% endlien %}

## Introduction

### Objectif

A travers ce MON je souhaite apprendre / réapprendre à faire un site web dynamique avec la gestion d'un serveur, en refaisant le projet numérologie pour comprendre les bases. Je souhaite surtout connaître le fonctionnement d'un back-end et la création de routes, ce qui sera utile dans une premier temps pour le projet 3A et plus lointainement pour mon stage.

### Principe

Le projet Numérologie consiste à créer un site web en suivant différentes étapes qui permettent d'illustrer le cours de web expliqué en parallèle sur le même site. Ce site est constitué d'une interface sur laquelle on peut rentrer un prénom et le serveur nous renvoie un chiffre associé à ce prénom ainsi qu'un petit texte associé à la spiritualité du chiffre.

{% note %}
Ce MON a déjà été réalisé par d'autres personnes comme Manuela ([MON de Manuela](https://francoisbrucker.github.io/do-it/promos/2024-2025/Manuela-Barreto/mon/temps-2.1/)) ou Jeanne ([MON de Jeanne](https://francoisbrucker.github.io/do-it/promos/2024-2025/Menager-Jeanne/mon/temps-2.1/))
{% endnote %}

## Sommaire

1. Front-end
2. Ajout du back-end
3. Gestion des données
4. Jardinage du code
5. Maintenance
6. Remarques générales
7. Conclusion

## Front-end

Je suis passée rapidement sur cette partie car j'ai déjà fait plusieurs projets pour apprendre à faire du front. J'ai simplement tout relu en diagonale et ai récupéré les fichiers statiques pour le projet pour être prête à faire le reste. Je note aussi que les bonnes pratiques surviennent après avoir déjà tout fait, je ne suis pas sûre d'avoir saisi pourquoi.

## Ajout du back-end

Dans cette partie sur laquelle je me suis beaucoup plus attardée, j'ai appris à construire un serveur node. J'ai passé beaucoup de temps à lire le cours sur les serveurs et à comprendre la gestion des routes avant de le mettre en application sur le projet Numérologie.

Ce que j'ai estimé important de retenir :

##### La gestion javascript des modules (es6 modules) VS celle de node (commonJS)

Ce qui implique deux styles d'écriture différents. Nous avons choisi la gestion javascript en rajoutant la ligne `"type": "module"` dans le fichier de configuration `package.json`.

##### La forme d'une réponse de requête http

- Le status code : indiquant si on a bien réussi la requête ou pas
- Le header indiquant le type de réponse
- La réponse en elle-même que l'on renvoie via le `res.end()`

##### Gérer les routes avec express

- `const app = express()` pour créer notre objet qui servira à faire les requêtes
- `app.use` VS `app.get` VS `app.post` pour les différents types de requêtes
- `res.redirect(302, "nouvelle/route/")` pour faire des redirections
- ... Voir le site directement

##### Créer des routes spéciales en encodant l'info dans l'url ou dans une query

- Dans l'url : `http://localhost:3000/prenom/lola` -> dans ce cas on fait un app.get de la forme `'/prenom/:valeur'` et on récupère le prénom avec `req.params.valeur`
- Dans une query : `http://localhost:3000/prenom?valeur=lola` -> dans ce cas on fait un app.get de la forme `'/prenom/'` et on récupère le prénom avec `req.query.valeur`

##### Faire une requête depuis le front

Se fait avec la fonction `fetch` suivi de l'url que l'on veut lire. C'est une promesse.

##### Le fonctionnement les promesses en javascript

`await` dans une fonction "async" ou `.then()` selon si on veut attendre ou pas un résultat avant de passer à la suite du code.

##### Utiliser des fichiers à différents endroits

Dans les fichiers dont on aura besoin ailleurs, comme le fichier qui permet de calculer le chiffre associé au prénom, on va rajouter un **export** auquel on rattache un objet que l'on peut appeler dans un autre fichier à condition de l'avoir **importé**. Cela ressemble à : `export default { chiffre: chiffreAssocie }` dans le fichier numérologie.js puis dans l'autre fichier : `import numérologie from './back/numérologie.js';` (attention : on importe avec un chemin relatif). On accède ensuite à la fonction avec `mumérologie.chiffre(...)`

## Gestion des données

Dans cette partie on apprend comment on fait habituellement pour gérer chaque composante de l'acronyme CRUD (create-read-update-delete). Généralement on a besoin que des requêtes get et post.

On passe très souvent par du JSON, dont l'équivalent est le blob pour les images.

Enfin, j'ai pu apprendre comment créer et agir sur une base de données SQLite avec l'ORM **sequelize**. A noter qu'on définit un fichier pour définir le modèle de la base, et un autre pour la synchronisation et l'initialisation.

## Jardinage du code

Cette partie consiste simplement à montrer comment écrire un code plus propre ce qui est je trouve intéressant et facile à suivre. Cette partie n'a pas de cours associé, enfin, c'est un peu comme un cours mais c'est accessible uniquement depuis le projet numérologie car on l'applique directement à ce projet.

- On y apprend qu'il est bien de **séparer la gestion des routes du serveur** selon leurs types, pour ne pas surcharger le fichier principal et le rendre plus lisible. Premièrement on sépare la gestion des routes non statiques et statiques. On gère les routes spéciales dans un fichier à part que l'on importe ensuite dans le fichier principal du serveur. Et dans un second temps on sépare aussi à l'intérieur des routes spéciales les routes API pour agir sur la bdd.

- Aussi on **sépare les différents modèles de la base de données** toujours pour rendre le code plus clair en utilisant une **injection de dépendance** c'est à dire qu'on exporte plus un dictionnaire mais une fonction dans laquelle on va passer notre bdd par la suite pour l'initialisation (plus simple à comprendre diretement sur le [cours](https://francoisbrucker.github.io/cours_informatique/cours/web/projet-num%C3%A9rologie/partie-4-jardinage/2-modeles/))

## Maintenance

Dans cette partie on aborde plusieurs aspects de la maintenance d'un site :

- On y explique dans un premier temps comment **mettre à jour les dépendance installées** pour le site via quelques commandes.
- Puis comment créer **des logs pour notre serveur**, je pense que c'est une partie intéressante pour savoir comment ça se passe un peu dans la vraie vie d'un projet car on n'y pense jamais. J'y ai appris des choses même si je sais que je ne vais pas retenir toutes les commandes spécifiques qui ont été utilisées pour le projet numérologie spécifiquement. J4ai compris le principe.
- L'importance de **faire des tests** et comment les faire même si ça va peut être un peu loin pour tout vérifier au fur et à mesure sans casser des choses.

## Remarques générales sur le site

L'arborescence du site n'est pas évidente à suivre, on navigue beaucoup entre les pages et on est souvent perdu sur le site. Ca pose problème notamment quand on veut se rappeler d'une information spécifique : on ne sait plus où aller. Aussi, c'est vrai qu'il est bizarre de travailler avec du code en "anglais" avec es noms de variables et de fichiers en français avec des accents, je me suis faite avoir plusieurs fois sur des problèmes de typologies.

Enfin, il y a quelques coquilles sur le code proposé tout au long du site, ainsi que quelques fautes de syntaxe / orthographe qui ne facilitent pas le déroulement du projet et sa lecture. En soi ce n'est pas très grave car cela nous force à bien comprendre le code pour voir où ca bloque, mais ça nous empêche de faire des copier-coller efficaces quand on veut aller plus vite.

{% details "Voir les quelques coquilles relevées" %}

Partie 1 :

- [ici](https://francoisbrucker.github.io/cours_informatique/cours/web/projet-num%C3%A9rologie/partie-1-front/niveau-1/2-code_js/), dans la définition de la fonction `somme(nombre)` la variable chaîne n'est pas déclarée (il manque le `let`)

Partie 2 :

- [ici](https://francoisbrucker.github.io/cours_informatique/cours/web/projet-num%C3%A9rologie/partie-2-serveur/2-javascript-serveur/), la fonction "nombre(chaîne)" (dans logique de conversion) pose problème, elle n'est pas copier collable il faut reprendre le code de la partie 1.
- [ici aussi](https://francoisbrucker.github.io/cours_informatique/cours/web/projet-num%C3%A9rologie/partie-2-serveur/2-javascript-serveur/), il manque les décarations des variables quand on paramètre les routes (`prénom =...` plutôt que `let prénom =...`)

Partie 3 :

- [ici](https://francoisbrucker.github.io/cours_informatique/cours/web/projet-num%C3%A9rologie/partie-3-donn%C3%A9es/1-base-de-donn%C3%A9es/) même chose dans la partie lecture de donnée il manque un `let` devant la variable `element`

{% enddetails %}

## Conclusion

Grâce à ce MON j'ai pu revoir les bases du back-end que j'avais mal comprises / oubliées. J'ai maintenant une vision plus claire et peut être une base plus solide qui me servira pour mes futurs projets avant de devoir utiliser tout de suite des frameworks. Cependant je vois bien qu'on ne recouvre qu'un petite partie de ce que l'on peut faire et il va falloir que je complète ces recherches pour trouver d'autres méthodes qui fonctionneront en fonction de mes projets.
