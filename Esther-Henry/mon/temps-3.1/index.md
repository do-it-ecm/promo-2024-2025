---
layout: layout/mon.njk

title: "HTML CSS : comprendre le web quand on est pas Dev Web"
authors:
  - Esther Henry

date: 1971-02-01
temps : 3
tags: 
  - "html"
  - "css"
  - "débutant"

résumé: "L’objectif de ce MON est de découvrir les langages HTML et CSS afin d’être capable de comprendre ces langages notamment pour comprendre de quoi parle les Dev."
---

{% prerequis %}

Aucun prérequis

{% endprerequis %}

## Apprendre les bases de HTML et CSS

### Contexte

Dans le cadre de notre Projet 3A, il est nécessaire que j’acquière les bases en HTML et CSS afin de contribuer à la création de notre site internet. De plus, je pense que, pour travailler dans le milieu de l’IT, il est fort utile de comprendre les bases de ces langages afin de pouvoir échanger plus facilement avec les développeurs avec lesquels on peut être amenée à travailler, d’où mon choix de découvrir les bases de HTML et CSS pour ce MON 3.1.

Pour notre Projet 3A, je veux réaliser la page de notre présentation et, pour cela, j’ai notamment besoin de savoir faire :  

- Une page internet (base des bases)  
- Sur laquelle mettre en page :  
- Différents blocs de textes (police, taille, couleur, disposition)  
- Des images (taille, disposition)  
- Des icônes  

### Cours suivi

Après avoir balayé les différents POK&MON existants à ce sujet sur le site de Do-It, il m’a semblé que le cours le plus adapté pour moi est : [Créez votre site web avec HTML5 et CSS3](https://openclassrooms.com/fr/courses/1603881-creez-votre-site-web-avec-html5-et-css3).

En effet, ce cours nous propose “un projet fil rouge” à réaliser en parallèle de l’apprentissage, qui semble coller aux besoins pour notre site, car il s’agit d’un site d’une professionnelle qui souhaite se présenter elle et son travail, ce qui correspond à mes objectifs.

### Retour critique

J’ai donc suivi les deux premiers chapitres ainsi que la moitié du troisième du cours (jusqu’à : “Faites votre mise en page avec Flexbox”) d’OpenClassrooms.

De mon point de vue, regarder les vidéos d’introduction puis lire les paragraphes de cours avant de s’exercer soi-même sur le projet fil rouge permet d’apprendre relativement vite les bases du HTML et du CSS tout en s’entraînant au fur et à mesure. Cela permet de rapidement vérifier si les notions sont comprises, ce qui m’a plu, et je pense que j’aurais difficilement pu apprendre autant de choses en ce temps en passant par un autre site. Je recommande donc ce cours à ceux qui, comme moi, veulent apprendre les bases du HTML et du CSS (peut-être que pour les plus verts, il existe des ressources plus complètes ?).

Ainsi, je pense qu’après avoir suivi ce cours, je pourrai bien répondre à mes objectifs, c’est-à-dire comprendre un peu mieux le web (du moins la structure d’un site internet et son langage de base). Je pourrai aussi participer activement à la réalisation de notre site pour le Projet 3A.

## Pratiquer : mon site/blog de voyage

### Contexte

Mon objectif n’étant pas de devenir développeuse web, j’ai choisi de pratiquer les connaissances déjà acquises plutôt que d’en apprendre encore plus au risque de tout oublier.

J’ai donc choisi de commencer à coder la base d’un site internet qui pourrait me servir de blog de voyage, car c’est quelque chose que j’aurais aimé faire en rentrant de césure, mais je ne m’étais jamais lancée. C’est donc l’occasion de commencer et de pratiquer mes bases de HTML/CSS apprises plus tôt.

### Réalisation

J’ai commencé par faire un brouillon de la structure de mon site, qui comportera trois types de pages : 

- Page de présentation  
- Page par pays  
- Page par destination/ville  

J’ai ensuite créé un dossier (en local) dans lequel j’ai placé un **dossier “images”**, et j’ai créé mes fichiers **”index.html”**, **”style.css”** puis **”bolivie.html”** (comme exemple de fiche pays).

Puis, j’ai repris les différentes notions vues dans les cours, notamment la structure d’un code HTML avec les notions de “header”, “body”, “main”, etc.

{% info %}
Comme il m’est arrivé plusieurs fois d’oublier : pensez bien à ajouter la ligne **```<link href="style.css" rel="stylesheet">```** dans les balises `<head>` de votre code HTML pour le lier avec le CSS.  
Sinon, comme moi, vous allez perdre du temps à croire que vos modifications du CSS ne fonctionnent pas, alors que vous ne les avez juste pas appelées dans le HTML. 🥲
{% endinfo %}

### Retour critique

✅ J’ai eu le temps de coder ma page d’accueil ainsi qu’une page pays.

❌ Pour l’instant, je ne suis pas satisfaite de l’aspect esthétique du site (une bonne maquette Figma serait nécessaire pour prendre le temps de réfléchir à la charte graphique). Ici, j’ai voulu me concentrer sur le HTML et le CSS, mais à l’avenir, j’aimerais prendre le temps de faire une maquette du site pour pouvoir le continuer sur mon temps personnel avec une base plus propre.

✅  Je n’ai pas eu le temps d’utiliser beaucoup de propriétés, notamment celles liées à l’apparence dynamique, mais j’ai pu réutiliser les propriétés de texte, image, fond, forme, et même de flex. Je suis donc contente d’avoir pu mobiliser ces connaissances sur un cas concret non guidé.

## Conclusion

À première vue, le HTML et le CSS me paraissaient être des termes bien barbares et bien trop verts pour moi, mais je suis contente de m’y être confrontée. Avec seulement quelques heures de travail, on arrive à faire quelque chose de concret et d’utile.

Par ailleurs, j’ai répondu à mes deux objectifs :

- Je vais être capable de participer activement à la suite de notre Projet 3A sur la partie site internet.
- Je suis maintenant capable de comprendre la structure de base du HTML (et du CSS), ce qui me permettra de mieux comprendre les développeurs, notamment dans le monde du travail.

### Horodatage

| Date | Heures passées | Indications |
| -------- | --------- | --------|
| Mercredi 15/01 | 3h | Bases HTML |
| Mercredi 15/01 | 3h | Bases CSS |
| Jeudi 15/01 | 1h | Agencer le contenu |
| Dimanche 19/01 | 3h | Exercice : mon site internet |

### Bibliographie

{% lien %}
[Créez votre site web avec HTML5 et CSS3](https://openclassrooms.com/fr/courses/1603881-creez-votre-site-web-avec-html5-et-css3)
{% endlien %}
