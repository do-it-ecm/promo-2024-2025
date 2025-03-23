---
layout: layout/mon.njk

title: "Créer un backend et le lier au frontend"
authors:
  - Ménager Jeanne

date: 2025-01-29
temps: 3
tags:

description: "Un MON traitant d'un sujet."
---

{% prerequis %}

Avec quelques connaissances et javascript et en frontend

{% endprerequis %}
{% lien %}

https://www.youtube.com/watch?v=InsdRTPy964
{% endlien %}

Je n'avais jamais créé de projet from scratch avec un backend et un frontend, je voulais donc savoir comment faire avec Vue.js pour le frontend et Node.js avec Express pour le backend pour pouvoir faire les 4 opérations classique (Create, Read, Update, Delete).

## Le backend

### Initialisation

1) faire npm init :
  Cela crée un fichier `package.json` où toutes les dependencies seront listées

2) Instalation des différents packages : express, nodemon, dotenv

3) Utiliser express pour créer le server `const app = express();`

4) Rajouter la commande `start` pour utiliser nodemon et ne pas avoir à relancer notre server à chaque modification

5) Découverte de Postman pour pouvoir tester les requêtes

### Création des premières routes

1) Création des route Get, Post, Put et Delete dans un dossier de route. Au début, elles renvoyaient juste un message pour voir que la commande fonctionnait bien mais sans base de données, elles n'avaient pas d'autre effet.

`router.route("/:id").get((req, res) => {
  res.status(200).send({message: 'Get all contacts'})
})`

Pour les tester, on peut utiliser postman.

2) Création de controllers pour que le code soit plus propre

Dans le controller, on commmence à gere les erreurs pour pas qu'on contact à qui il manque une info soit créé

3) Le middleware

On créee `errorHandler` pour mieux gérer les erreurs et avoir des messages d'erreur associés à chaque type d'erreur

### MongoDB

J'ai utilisé Atlas qui est en ligne, j'ai créé un projet et un cluster.
Il fallait ensuite le connecter au backend mais j'ai eu beaucoup de problème et j'ai suivi plein de conseil qui me suggéraient des étapes pour que cela fonctionne mais sans succès. Finalement, je me suis connectée au wifi à la place de mon partage de connexion et ensuite, je n'avais plus d'erreur d'adresse IP.

Pour connecter mongoBD, il faut créer un fichier `connection.js` dans lequel on importe mongoose.

### Création du model

Grace à `new mongoose.Schema`, on définit les différents champs qui nous intérressent, exemple : pour chaque contact, on souhaite avoir le nom, l'email, le numéro de téléphon et le métier dans l'exemple de la vidéo.

### Modification de controller

Maintenant, qu'on a une DB, on peut créer de vraies routes qui vont ajouter, modifier, supprimer ou lire des données.

Pour créer par exemple : `contact.create({name, email, phone, designation})`

De nouveau, on peut tout tester grâce à Postman et on peut voir dans Atlas la liste de nos données.

À ce moment, j'ai créer 5 routes.


## Le Frontend

La deuxième partie de la vidéo traitait de comment utiliser notre backend pour visualiser les données dans le frontend.

1) npx create-vue@latest : crée automatiquement un frontend avec des pages prédéfinies par vue que l'on va supprimer pour faire nos propres pages.

Le frontend se lance grâce à `npm run dev`


2) Creation de plusieurs components pour avoir plusieurs pages sur le site. On crée aussi un header grâce à bootstrap.

3) Utilisation de axios :
Axios nous permet d'acceder aux routes du backend pour par exemple récuperer tous nos contacts. On fait tout ca en faisant attention à la gestion des erreurs grâce à des `try{...} catch(err) {...}`


4) création de page pour ajouter et modifier les contacts: on utilise axios et pour la modification, il faut qu'on récupère l'id du contact

5) La suppression : grâce à l'id aussi

Remarques: On a utilisé `toast` pour envoyé des petites notification spour que l'utilisateur se rende compte des actions effectuées.
On a aussi utilisé un loader de vue pour rendre la navigation plus agréable.

## Conclusion

Il faut choisir une vidéo recente car tout change très vite et j'ai perdu beaucoup de temps avec des vidéo plus anciennes

Le site crée n'est pas très beau mais l'objectif ici était de réussir à afficher les données du backend

