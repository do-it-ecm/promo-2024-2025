---
layout: layout/pok.njk

title: "Scraping"
authors:
  - Alix Duréault

date: 1971-03-01

temps: 3
tags:

résumé: Un POK traitant d'un sujet.
---

{% prerequis %}

Des bases en python sont nécessaires pour ce POK.

{% endprerequis %}
{% lien %}

Les lien utiles pour la compréhension de celui-ci.

{% endlien %}

Pour mon projet de filière métier, nous réalisons un bilan carbone. Pour cette structure, beaucoup d'informations sont disponibles sur leur site web. Ainsi, pour pouvoir faciliter la récupération de données, j'aimerais apprendre le scraping et comment l'utiliser pour récupérer des données qui sont utilisables et complétables par la suite.

## Tâches

### Sprints

#### Sprint 1

- [x] Qu'est ce qu'est réellement le scraping ?
- [x] Apprendre les bases du scraping
- [x] Quelles en sont les limites
- [ ] Coder la récupération des données

#### Sprint 2

- [ ] Algorithme de récupération des données
- [ ] Traitement des données
- [ ] Travail sur l'utilisation des données

### Horodatage

Toutes les séances et le nombre d'heure que l'on y a passé.

| Date | Heures passées | Indications |
| -------- | -------- |-------- |
| 14/01 | 30 min | Lecture des mons précédents sur le sujet et étude rapide du site à scraper |
| 16/01 | 1 h | Définition du scraping et recherches sur ces limites |
| 17/01 | 2 h | Suivi d'une formation sur le scraping |
| 20/01 | 1 h 45 | Suivi d'une formation sur le scraping |
| 22/01 | 2 h | Suivi d'une formation sur le scraping |
| 23/01 | 1 h 15 | Suivi d'une formation sur le scraping |
| 27/01 | 1 h 30 | Suivi d'une formation sur le scraping |

## Contenu

### Premier Sprint

#### Le scraping

Pour comprendre un peut mieux de quoi il en retourne, j’ai commencer par lire l’article de Cloudflare sur le sujet : [Qu'est ce que le scrping de données ?](https://www.cloudflare.com/fr-fr/learning/bots/what-is-data-scraping/).

Ainsi, le craping de données est une technique qui permet, à l’aide d’un programme informatique, d’extraire des données d’un autre programme, généralement celui d’un site web.

Il y a trois étapes clés au scraping : 

1. Envoie d’une requette http GET à un site web
2. Analyse du document HTML reçu
3. Extraction des données et conversion dans un certain format

Le scraping est le plus souvent utilisé pour récupéré du contenu spécifique d’un site web, des prix ou encore des contacts.

#### Légalité du scraping

Pour comprendre ce sujet, j’ai lu l’article de datadome : [Le web scraping est-il illégal ?](https://datadome.co/fr/guides-fr/scraping-fr/le-web-scraping-est-il-illegal/) et regardé la vidé de Fireship : [Am I going to jail for web scraping ?](https://www.youtube.com/watch?v=8GhFmQPZAlo).

Dans la plupart des pays, le web scraping n’est pas illégal. Cependant l’utilisation des données récoltées peut être punissable juridiquement. Et il faut rester attentif, certains sites restreignent ou interdisent explicitement le web scraping sur leurs données.

Les activités liées au webscrping qui sont à la limite de la légalité sont les suivantes : 

- Se connecter à un site web et télécharger des données
- La collecte de données personnelles ou des informations sensibles sans consentement
- Le scraping de contenu protégé par des droits d’auteur ou propriétaire sans consentement explicite
- Le scraping des données à partir de zones restreintes ou privées d’un site web
- Revendre ou distribuer les données récupérées
- La collecte de données à des fins discriminatoires, contraires à l’éthique, ou malveillantes
- Le scraping non autorisé de sites web ou de bases de données gouvernementales

En France, certaines de ces activités sont concernés par le RGPD, notamment tout ce qui consiste en la récolte de données personnelles sans consentement explicite.

#### Apprendre le scraping de données

Pour apprendre à scraper, j’ai utiliser la formation proposée par Docstring : [Scraping avec Python : Formation complète 2024](https://www.youtube.com/watch?v=sOAZpHDEdkg)

### Second Sprint
