---
layout: layout/pok.njk

title: "POK 2 - Pass' Diplôme"
authors:
  - Alix Duréault

date: 2024-10-16

temps: 2
tags:
  - "info"

description: Ce second POK réalisé en collaboration avec Ines Kebbab a pour objectif de réaliser un SI pour suivre et communiquer les items de diplomation, en collaboration avec la formation de l'école.
---

{% prerequis %}

Pour ce POK, je me suis basé sur des connaissances en React, HTML, JS et Figma.

{% endprerequis %}

{% lien %}

Ce POK est en lien avec mon [MON du temps 2.1]({{ site.url }}/promos/2024-2025/Alix-Dureault/mon/temps-2.1/).

{% endlien %}

## Objectifs

Nous avons pu remarquer qu'il arrive chaque année que des élèves ne sont pas au clair de ce qui leur reste à valider, que des erreurs se glissent dans les preuves de validation mais ne sont remarquées que peut avant le jury. Suite à ce constat, nous avons discuter avec Catherine Musy pour voir si il était possible de rendre ce type d'informations accessibles aux élèves. Le problème est que toutes ces informations ne sont regroupées qu'au dernier moment, juste avant les jurys.

L'objectif de ce POK est donc de réaliser un système d'information sur un exemple concret, via une base de données (excel et site internet) tout en respectant des contraintes RGPD. Concrètement, les élèves doivent pouvoir consulter les éléments qui les concernent exclusivement.

Ce projet a aussi pour but d'observer les enjeux de management de l'information au sein des services de l'école dans le cadre d'un projet, notamment pour la mise en place d'un process qui se veut durable.

À noter, nous nous sommes engagées en termes de moyens et non de résultat.

## Tâches

### Sprint 1

- [ ] Réalisation d'un excel et étude de l'automatisation possible
- [x] Réalisation d'une maquette du site souhaité
- [x] Etude des technologies compatibles avec la DSI de Centrale
- [x] Initialisation d'une base de données test

Après la réunion de cadrage et la réunion avec la DSI, nous avons pu constater que nous n'avions pas besoin de faire un excel détaillé et automatisé. Le coeur de notre tâche ce concentre donc surtout sur le site web qui permet à la gestion de scolarité de mettre à disposition des élèves les informations concernant leurs critères de validation pour leurs diplômes.

### Sprint 2

- [x] Front-end du site
- [ ] Proposition du nouveau process aux équipes
- [ ] Back-end du site (+ connexion au CAS si accepté par la DSI)
- [ ] Mise en conformité RGPD
- [ ] Communication à destination des élèves sur le projet

La prévision de tâches avant le sprint était particulièrement optimiste. La première erreur qui a été faite est de ne pas l'avoir revu à la baisse à l'issue du Sprint 1 où on aurais pu se rendre compte avec Inès que la charge de travail était démesurée. Ensuite, nous avons probablement était autant optimistes par manque de connaissances de comment fonctionne React et comment créer un back et une connexion via cas. Le projet semblait extrèmement plus simple que il ne l'est réellement.

### Horodatage

| Date | Heures passées | Indications |
| -------- | -------- |-------- |
| Réunion de cadrage | 1h | 18/10/2024 |
| Réunion avec le CRI | 1h | 24/10/2024 |
| Première maquette rapide du site | 20 min | 24/10/2024 |
| Mise en forme base de donnée test | 40 min | 13/11/2024 |
| Recherche sur la database | 50 min | 15/11/2024 |
| Travail sur la maquette | 50 min | 16/11/2024 |
| Travail sur la maquette | 1h10 min | 17/11/2024 |
| Recherche sur la database | 20 min | 17/11/2024 |
| Création du repository github et initialisation du front sur React | 30 min | 17/11/2024 |
| Réunion de mi-parcours (validation maquette) | 1h | 18/11/2024 |
| Travail sur la maquette | 40 min | 18/11/2024 |
| Ajout de la validation de donnée sur l'excel | 10 min | 18/11/2024 |
| Traitement des infos des différentes réunions | 30 min | 18/11/2024 |
| Receuil d’avis des élèves sur le design | 1h | 19/11/2024 |
| Travail sur le front du header du site | 2h30 | 04/12/2024 |
| Travail sur le front du contenu élève | 1h30 | 05/12/2024 |
| Travail sur le front du contenu élève | 2h | 08/12/2024 |
| Réunion de suivi du projet avec Catherine Musy | 1h | 09/12/2024 |
| Réunion de suivi du projet avec Clément Leneveu | 1h | 12/12/2024 |
| Travail sur le front du contenu élève | 1h | 14/12/2024 |
| Travail sur le front du contenu élève | 1h | 17/12/2024 |

## Premier Sprint

### Choix des technologies

Nous avons pu choisir les technologies suite à notre réunion avec la DSI.

Pour pouvoir nous aider, ils nous ont conseillé d'utiliser des frameworks JavaScript comme React ou Angular ou des frameworks Python.

Pour le front, nous utilisons toutes les deux React pour nos projets, il nous a donc semblé une bonne idée de l'utiliser aussi lors de ce projet.

### Quelle forme aura la base de donnée du site ?

Actuellement la gestion de la scolarité travaille sur un excel sur lequel sont présents tous les élèves. Pour faciliter l'implémentation du site, nous voulions changer leurs habitudes le moins possible. Ainsi nous voulions garder le travail sur excel pour ces personnes. Après discussion avec la DSI, nous avons compris l'importance d'avoir un chemin entre cet excel et la base de donnée et une validation de donnée sur l'excel, les erreurs pouvant être trop fréquentes.

Ainsi, nous avons opté pour une solution où l'excel sera rempli comme précédemment mais une fois que cela est fait, la personne référente peut le télécharger en csv et aller l'importer sur le site directement.

Cela implique plusieurs choses derrière sur notre travail :
- Devoir coder une interface pour ces interlocuteurs
- Prévoir une gestion des droits afin de palier au turn over des personnes référentes
- Trouver la solution technique pour importer un fichier csv sur le site et remplacer la base de donnée

### Solution technique pour la base de donnée

J'ai pu exercé quelques recherches sur le sujet en décomposant le sujet en plusieurs étapes :
1. Upload d'un fichier csv à partir de l'interface du site web

Au cours de mes recherches, j'ai pu trouvé plusieurs ressources qui pourront nous aider dans cette tâche : [Upload un fichier dans React](https://www.youtube.com/watch?v=ijx0Uqlo3NA), [Upload un fichier dans React avec une barre de progrès ](https://www.youtube.com/watch?v=edR6Az7shv8) et [Upload un fichier avec une API drag and drop](https://www.youtube.com/watch?v=vEkf9JgJV00).

2. Effacement de la base de donnée existante

Cela sera à priori assez simple. J'ai tout de même trouver une ressource au cas où : [UPDATE et DELETE de la donnée dans une table MySQL](https://www.youtube.com/watch?v=OB2leB2iZ6U&pp=ygUXZGVsZXRlIGRhdGEgaW4gZGF0YWJhc2U%3D).

3. Lecture du fichier csv pour remplacer la base de donnée

Au moment où j'ai fais les recherches, je ne savais pas encore quelle technologie nous allons utiliser, j'ai donc trouver des ressources sur différentes options : [Importer un fichier CSV sur MySQL](https://www.youtube.com/watch?v=INtejSjK5w0) et [Importer un fichier CSV sur SQLServer](https://www.youtube.com/watch?v=8HWXjh6eBjc).

### Quel sera le visuel des différentes interfaces du site ?

Pour cela, j'ai travaillé sur une première visualisation sur les différentes vues élèves (elles dépendent du parcours à Centrale) et sur la vue admin.

![Première maquette](./Maquette_v0.jpg)

Ensuite Ines a pu travaillé sur une deuxième version plus élaboré.

Enfin après les retours de Catherine Musy, j'ai pu reprendre quelques éléments et ajouter la vue administrateur.

![Première maquette](./Maquette_v2.jpg)

### Initialisation de l'excel côté gestion de la scolarité

Pour se donner une bonne idée de à quoi ressemble l'excel avec lequel travaille la gestion de la scolarité, Catherine Muzy a pu nous envoyé un extrait anonymosé du tableau de diplomation de cette année.

Je l'ai par la suite modifié pour qu'il convienne plus aux différents service (BIP et Bureau 2A). J'ai aussi pu ajouter plusieurs lignes tests d'élèves consentants qui nous permettront de mener les tests de connexion à la fin du projet.

### Comment le visuel est reçu par des élèves et la gestion de la scolarité ?

Enfin, après le travail de maquette, je suis aller voir un petite dizaine d'étudiants afin d'obtenir leur avis sur la maquette. Le but de ce travail était de comprendre si elle était lisible et compréhensible et quel type de légende est nécessaire.

Inès a pu travaillé sur la prise en compte de ces avis. Globalement, ces avis nous amènent à retravailler la présentation des crédits ECTS, quelques formulations et la présence du stage de deuxième année en fonction du parcours de l'élève.

## Second Sprint

 Pour le second sprint, j'ai pu me concentrer sur commencer à coder notre application.

### Comment transcrire un design depuis Figma à un code React ?

Pour commencer, j'ai décidé de diviser le travail en étapes et éléments. Ainsi, au début, j'ai fait le choix de commencer par coder seulement le visuel. Dans un second temps, on ajoutera les changements de design en fonction des valeurs dans les différentes cases, les liens avec la base de données, le lien avec le CAS. J'ai aussi fait le choix de commencer par un élément très précis qui est le header puis de continuer sur la page élève classique qui pourra être modulée en fonction des parcours.

Ainsi, j'ai commencé par coder le header qui est utilisé dans toutes les pages du site. Puis j'ai enchaîné sur le code de la page pour les étudiants.

### Comment coder le header ?

Pour faire le header, cela a été assez simple. En html, j'ai séparé avec des balises `<nav>` le côté droit et le côté gauche.

Puis je suis passée au code css. Dans celui-ci, j'ai commencé par ajouter les éléments généraux : le background blanc, l'initialisation des marges de la page et les polices pour les titres et les paragraphes.

Pour le header, j'ai commencé par ajouter les couleurs du background et du texte. J'ai ensuite utilisé une flexbox afin de pouvoir aligner les différents éléments. Enfin, j'ai dimensioné les différents éléments avec les bonnes proporsions, ajouter des marges pour les distancer et utilisé les propriétés `align-items` et `justify-content` afin de les placer au bon endroit et de les aligner.

Pour visualiser :
- le design Figma
![Header designé sur Figma](./Header_Figma.jpg)
- le design React
![Header codé sur React](./Header_React.jpg)

On peut remarquer quelques différences entre les deux designs. Cela est du au travail qu'à pu effectué Inès pendant que j'étais en train de coder et que je n'ai pas encore eu le temps d'intégrer.

Une fois le header fini, j'ai commencé à coder le contenu élève.

### Comment traduire la page élève de Figma à React ?

Pour cela j'ai décomposé la page en trois éléments que j'ai codé un à un.

J'ai commencé par le "header", la barre qui contient les informations sur le parcours de l'élève. Il s'agit d'un simple titre sur lequel j'ai ajouté un backgroud, une taille et un padding.

Ensuite, je suis passée aux cases Formation et Stage. J'ai suivi à peu près le même process pour les deux boxs.

Simplement, j'ai crée une border pour la box entière puis j'ai designé le header avec un background, une flexbox pour aligner le logo information et le titre, la couleur et la taille du titre et du logo information.

Une fois le début des cases réalisées, j'ai utilisé la propriété flexbox pour aligné la boîte formation et la boîte stage. Puis j'ai réglé leurs width afin qu'elles fassent la bonne taille pour la page.

Enfin, il s'est agi de designé le contenu de ces boîtes. J'ai commencé pas utilisé une flexbox mais cela ne s'est pas avéré très efficace. J'ai donc changé cette solution par une autre, l'utilisation de la propriété `grid`. Une fois cette propriété mise en place avec des balises `<nav>` et `<div>` bien placé dans le fichier jsx, je n'ai plus eu qu'à ajouter le style des textes et des infographies.

Poue visualiser :
- - le design Figma
![La page élève designée sur Figma](./Vue_eleve_Figma.jpg)
- le design React
![La page élève codée sur React](./Vue_eleves_React.jpg)