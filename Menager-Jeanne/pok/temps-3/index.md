---
layout: layout/pok.njk

title: "Créer un site internet format téléphone"
authors:
  - Ménager Jeanne

date: 2025-01-29

temps: 3
tags:

résumé: Un POK traitant d'un sujet.
---

{% prerequis %}

Javascript, vue.js, node.js

{% endprerequis %}
{% lien %}

- [MON sur la création d'un projet](/promos/2024-2025/Menager-Jeanne/mon.temps-3.1/index.md)

{% endlien %}

Je souhaite créer un site web adapté aux téléphones portables pour pouvoir suivre mes habitudes notamment de sport et d'alimentation et avoir des statistiques à ce sujet parce que ça m'interesse.

## Tâches

### Sprints

Pour mon Pok, l'idée est de pouvoir quantifier certains événements de notre vie en remplissant un Tracker tous les jours. Par exemple, j'essaye de reduire ma consommation de viande mais je ne me rends pas compte de combien de repas végétariens je fais sur le mois. En renseignant sur mon nouveau site internet tous les jours si j'ai mangé végétarien ou pas le midi et le soir, je pourrai avoir des statistiques. De même, si je souhaite me rendre compte de combien de fois par mois je prends le métro et combien de fois je prends le bus ou la voiture, mon POK pourra être utile.

#### Sprint 1

- [X] Créer le projet grâce à ce que j'ai appris dans mon MON
- [X] Créer les premieres routes
- [x] Créer un figma

En suivant le même tutoriel que pour mon MON (mais avec cette fois l'expérience de ce qui fonctionne ou pas), j'ai pu créer le backend du projet et le lier au frontend. 

Mon projet est donc initialisé mais pas du tout conforme à ce que je souhaite. 

J'ai créé un [figma](https://www.figma.com/design/92Y5pzepo2KpIlzudtkAqI/POK3?node-id=0-1&p=f&t=oMjlGDYY29ltTzAK-0) pour avoir une première idée de ce que je souhaite comme fonctionnement.

J'ai réfléchis plus efficacement grâce à ce figma pour pouvoir créer le model et commencer à l'implémenter.

#### Sprint 2

- [X] Créer le frontend
- [ ] mettre en ligne le site

Afin de coder le frontend, j'ai voulu utiliser la librairie 'quasar' qui permet d'avoir facilement des ici-ons, des pop-up et certains style pour le frontend. 
J'ai donc du installer cette librairie mais je me suis rendue compte que l'initialisation que j'avais fait dans le sprint 1 du frontend n'était pas compatible. J'ai donc cu recréer le frontend de mon projet. 

J'ai commencé par créer la page d'accueil (avec les tracker du jour) d'abords sans utiliser de donner du backend puis j'ai lié mon frontend à mon backend. 
J'ai ensuite ajouté le bouton pour ajouter un nouveau tracker.
J'ai ensuite implémenter les flèches pour passer de 'Aujourd'hui' à 'Demain', 'Hier' et aux autres dates, pour cela, j'ai utilisé la librairie 'moment js'. J'ai eu du mal à géré la réactivité mais grâce à un watcheur, j'ai pu régler le problème. 
J'ai ensuite implémenté les choix du tracker pour que ca s'enregistre dans la db. 

Enfin, j'ai implémenté la page de récap, pour laquel, j'ai pu réutilisé des composents que j'avais déjà créer. 

J'ai en effet créer un composant pour les petits carrés afin de pouvoir le réutiliser facilement mais aussi un pour les noms des options. Cela m'a grandement aidé à avoir un code plus clair. 

Je n'ai pas eu le temps de finir mon projet : en effet, il faudrait y rajouter un moyen pour l'utilisateur de se connecter et deployer le site. 

Quand à la partie statistique, je l'ai traitée dans mon MON. 

### Difficultés rencontrées : 
- Initialisation du projet différente si utilisation de quasar
- gestion des fonctions asynchrones pas facile avec la composition API de vue 3 

### Horodatage

Toutes les séances et le nombre d'heure que l'on y a passé.

| Date | Heures passées | Indications |
| -------- | -------- |-------- |
| Samedi 25/01  | 2H  | Initilisation du projet |
| Dimanche 26/01  | 2H  | Figma |
| Mardi 28/01  | 3H  | Création du model de données |
| Mercredi 5/03  | 1H  | Ré-initialisation pour pouvoir utiliser qausar |
| Jeudi 6/03  | 1H  | Création du menu |
| Jeudi 6/03  | 3H  | Création de la page d'accueil |
| Jeud 6/03  | 1H  | Modification du model de données pour qu'il corresponde à mes objectifs|
| Vendredi 7/03  | 1H  | Mise en place des flèches pour changer de date |
| Vendredi 7/03  | 1H  | Création de la popup d'ajout de tracker |
| Mardi 28/09  | 3H  | Création de la page de récap |

