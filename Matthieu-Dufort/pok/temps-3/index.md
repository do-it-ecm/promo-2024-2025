---
layout: layout/pok.njk

title: "La RGPD "
authors:
  - Matthieu Dufort

date: 2024-12-13

temps: 3
tags:
  - "RGPD"

résumé: Un POK traitant du Réglement Général sur la Protection des Données, de son évolution, et de son application dans le monde du digital.
---

{% lien %}

- [Texte Réglement Général sur la Protection des Données](https://www.cnil.fr/fr/reglement-europeen-protection-donnees)
- [Texte de la directive ePrivacy](https://www.legifrance.gouv.fr/jorf/id/JORFTEXT000000337468)
- [Texte du réglement AI Act](https://eur-lex.europa.eu/legal-content/FR/TXT/?uri=CELEX:32024R1689)

{% endlien %}

Ce pok à pour objectif de parcourir les régulations misent en place dans le monde pour protéger les données des utilisateurs. Il va aussi retracer dans un second temps les procès et attaques qui ont eu lieu contre les grandes entreprises du digital. Nous allons aussi essayer de comprendre comment peut-on protéger ses propres données.

## Tâches

### Sprints

Le but final de ce pok est d'acquérir de vrais connaissances sur le RGPD et de mieux comprendre les procès et enjeux actuelles autour de ceci.

#### Sprint 1

- [x] Retracer les débuts de le RGPD
- [x] Suivre l'évolution des régulations
- [x] Analyser les grosses différences de régulation dans le monde
- [x] Comprendre l'impact de ses différences sur les entreprises
- [x] Observer les moyens mis en place pour le contrôle de son application

#### Sprint 2

- [ ] Etude de cas du procès de la CNIL à l'encontre de GOOGLE LLC
- [ ] Etude de cas de la fuite de données récentes chez free

### Horodatage

| Date | Heures passées | Indications |
| -------- | -------- |-------- |
| dimanche 26/01 | 3H  | Origine RGPD et texte 2018 |
| lundi 27/01 | 2H  | texte et Evolution |
| mardi 28/01 | 4H  | Comparaison mondiale, Impact et controle des entreprises |
| mercredi 29/01 | 1H  | controle sur entreprise internationalle |

## Contenu

### Premier Sprint

## L'origine du RGPD

Le RGPD est un texte juridique de l'union européenne qui est entré en vigueur le 25 mai 2018 poour renforcer la protections des données personnelles des individus au sein de l'UE.

Avant le RGPD, c'était la Directive 95/46/CE qui dictait les règles minimales de la protection de données. Mais, celle-ci fu vite dépassé en raison de 3 causes principales :

- Fragmentation des règles (déclinaison de la directive dans le droit de chaque pays membre)
- Portée limitée (uniquement pour les entreprises étant établies physiquement dans l'UE)
- Faibles sanctions

Le passage à un réglement (au lieu d'une directive) permet une application directe dans tous les pays européens.

## Fondamentaux

Le RGPD est basé sur trois grands axes en 2018 :

### Droits des citoyens

Le RGPD place les citoyens au centre de la protection des données personnelles et leur offre plus de controle sur leurs données

- **Droit à l’information** : Toute entreprise doit informer clairement les individus sur la manière dont leurs données sont collectées, utilisées et protégées.
  
- **Droit d’accès** : Tout individu peut demander à une entreprise une copie de ses données personnelles.
  
- **Droit à l’effacement** : Tout individu peut demander la suppression de ses données dans certaines conditions (Comme en cas de données obsolètes ou si elles ne sont plus nécessaires).
  
- **Droit à la portabilité des données** : Tout individu peut récupérer ses données dans un format structuré pour les transférer à un autre prestataire.
  
- **Droit d’opposition** : Tout individu peut s’opposer au traitement de ses données, notamment à des fins de prospection commerciale.

### Responsabilités des entreprises

Le RGPD impose aux entreprises des obligations strictes pour garantir la protection des données personnelles, avec un principe de responsabilité.

- **Transparence et Consentement** : Toute organisation doit recueillir le consentement explicite des utilisateurs avant de collecter leurs données. Les termes et conditions doivent être clairs, compréhensibles et sans ambiguïté.
  
- **Obligation de sécurité** : Toutes entreprises doit protéger les données contre tout accès non autorisé, perte ou piratage en mettant en place des mesures techniques et organisationnelles adaptées. En cas de violation de données, elles doivent notifier l’incident à l’autorité compétente (comme la CNIL en France) dans les 72 heures.
  
- **Nomination d’un Délégué à la Protection des Données (DPO)** : Toute entreprise traitant des volumes importants de données sensibles (dépend de la nature des données) doit désigner un DPO chargé de veiller à la conformité au RGPD.
  
- **Documentation et analyses d’impact (PIA)** : Les entreprises doivent documenter leurs traitements de données et réaliser des analyses d’impact pour identifier et limiter les risques liés aux données personnelles.

### Harmonisation et sanctions dissuasives

Le RGPD introduit un cadre légal unifié pour toute l’Union européenne et impose des sanctions significatives.

- **Sanctions financières sévères** : Les entreprises en infraction peuvent encourir des amendes pouvant atteindre 20 millions d’euros ou 4 % de leur chiffre d’affaires annuel mondial (le montant le plus élevé étant appliqué).

- **Harmonisation des règles dans l’UE** : Le RGPD remplace les lois nationales fragmentées par une réglementation unique et directement applicable dans tous les États membres, simplifiant la conformité pour les entreprises opérant dans plusieurs pays.

- **Rôle des autorités de contrôle** : Chaque pays membre dispose d’une autorité de contrôle (comme la CNIL en France) pour veiller à l’application du RGPD et assister les citoyens en cas de non-respect de leurs droits.

## Evolution

Depuis la diffusion de ce texte, il y a eu très peu d'évolution législative. Cependant, ce texte a permis des évolutions de mentalité et de la prise de conscience des utilisateurs. En ce moment, il a cependant des discussion pour ajouter des textes complémentaires pour palier aux nouveaux défis techologiques.

### Evolution des mentalités

Du coté des citoyens :

- Les citoyens utilisent beaucoup plus qu'avant leur droit de rectification et suppression des données.
- Entre 2017 et 2018, le nombre de plainte déposé à la CNIL (Comission National de l'Informatique et des Libertés) à augmenté de 32.5% contre une évolution entre 2016 et 1017 de seulement 11%.

Du coté des entreprises :

- Les sanctions ont fortement évolué grâce au RGPD (+330% en 1 an), forçant les entreprises a suivre le nouveau réglement.
![Montant des sanctions liées au RGPD](https://i0.wp.com/novatek-consulting.com/wp-content/uploads/2020/04/amendes.png?w=400&ssl=1) *Graphique de l'évolution des sanctions RGDP, Novatek Consulting*
- Adoption des mesures techniques et organisationnelles évoquées dans le texte
- La bannière permetttant d'accepter ou de refuser les cookies est devenu standard et le nombre de refus à fortement augmenté.

### Des textes en cours de discussion

**Réglement ePrivacy**

Actuellement, comme le RGPD précédement, ce réglement n'est encore qu'une directive qui est donc modulable dans la loi nationale de chaque pays. C'est la directive : **2002/58/CE**. Il est débatut en ce moment afin de devenir un réglement.

Le ePrivacy est un ensemble de règles qui complètent le RGPD en se concentrant spécifiquement sur la confidentialité des communications électroniques. Il a pour objectif de protéger la vie privée des utilisateurs dans le cadre de l’utilisation des services de communication en ligne, tels que les e-mails, les SMS, les appels téléphoniques, et les cookies.

Il comprend des règles sur les sujets suivant principalement :

- Consentement pour les cookies
- Protection des communications électroniques
- Marketing électronique et prospection
- Confidentialité des métadonnées
- Régulation des communications non sollicitées
- Envoi de cookies tiers et traçage

**AI Act**

Ce réglement a été validé le 13 juin 2024 et comprend un ensemble de règle sur l'IA. Il vise à encadrer l'utilisation de l'intelligence artificielle (IA) dans le but de garantir la sécurité et les droits fondamentaux des citoyens tout en favorisant l'innovation.

Il défini :

- Un classement des IA par risque en fonction de leur but afin de les réglementer
- L'interdiction ertain usage et des obligations pour les IA de risque élevé
- Des exigences de transparence
- Des règles de gouvernance et de supervision
- Sanctions
- La mise en place de laboratoire réglementaire pour pousser à l'innovation

## Comparaison avec d'autres réglementations

Le RGPD est un référence à travers le monde en matière de protection de donnée. Certain pays ou état s'en inspire même pour créer leur propre système de protéction de donnée.

### Etat-Unis

Au Etat-Unis, il n'existe actuellement pas de texte fédéral régulant la gestion des données personnelles globales, chaque état est donc libre de fixer ses propres lois sur ce sujet. Les seuls données protégées par la loi sont celle sur la santés et les finances avec le *Health Insurance Portability and Accountability Act* et le *Gramm-Leach-Bliley Act*.

La différence de texte entre chaque état (+ de 600 lois différentes) rend difficile l'instauration d'un texte fédéral même si l'idée avait été énoncé en 2018. L'état Californien est le plus avancé en matière de protection de données personnelles grâce au *California Consumer Privacy Act* qui est fortement inspiré du RGPD.

### Chine

Le gouvernement chinois a mis en place un texte similaire au RGPD nommé la PIPL : **Personal Information Protection Law**. Les utilisateurs ont des droits semblable a ceux en Europe et les entreprises doivent avoir le consentement des utilisateurs et protéger les données.

Il existe cependant quelques différences comme :

- Des règles très strictes pour les entreprises étrangères traitant des données de citoyens chinois
- Les sanctions de ce texte reste plus faible
- Le gouvernement chnois peut accéder à plus de données en raison de question de sécurité nationale
  
### Général

Dans l'ensemble, tous les pays du monde ont aujourd'hui des règles sur la régulations des données similaires qui sont souvent comparable à celui du RGPD. Cependant, bien qu'il ait influencé de nombreuses législations, chaque pays ou région adapte ses lois en fonction de ses besoins spécifiques, de sa culture et de ses priorités en matière de protection des données. L'une des différences majeures réside dans la manière dont les pays équilibrent la protection des données avec des préoccupations telles que la sécurité nationale ou l'innovation technologique. Il reste aussi un des plus sévère en matière de sanctions financières.

## Adaptation des entreprises ces différences

Il existe pour les entreprises différentes façon de gérer ces changements de texte :

- Approche centralisée : se base pour tous leurs clients sur le texte le plus stricte (souvent le RGPD)
- Approche localisée : gestion locale en fonction de chaque texte

Concernant le stockage des données, il y a aussi plusieurs tendance :

- Stockage localisé : stocker les données dans un data center local (obligatoire en chine)
- Transfert autorisé :  des accords existe entre certain pays présentant des lois similaires (Europe/Japon...) avec cryptage des données pour les transferts

Concernant la gestion de données, c'est le même scénario :

- Equipe locale de management pour l'approche localisée
- Equipe globale pour l'approche centralisée
- Equipe locale de gestion de crise pour être dans les délais juridiques de chaque pays

Devant toutes ces différences, certaines entreprises appellent demandent un cadre internationnal tandis que d'autre profite des avantages présentés par ces différences pour exploiter au maximum chacunes des données.

## Contrôle de l'application du RGPD

Chaque pays européen détient une autorité de protection (comme la CNIL en France) des données qui réalise des contrôles, enquête, audit... afin de vérifier la bonne application du RGPD. Elles ont pour missions :

- Mener des contrôles pour vérifier la conformité (en ligne et physique).
- Répondre aux plaintes des citoyens.
- Émettre des sanctions en cas de non-respect du RGPD.
- Évaluer les entreprises sur la protection des données.

Pour cela, elles peuvent utiliser plusieurs outils :

- Analyse de site web et des cookies
- Investigation sur entreprise
- Demande de document (politique de gestion, contrats, registres...)

Et elles peuvent ensuite appliquer différents types de sanctions qui peuvent bien sur se cumuler :

- Sanction financière (20 millions ou 4% du CA mondial)
- Obligation de mise en conformité (avec délai imposé)
- Restriction des activités

Et ceci est valable pour toute entreprise gérant des données de citoyens européens.

{% details "Bilan Sprint 1" %}

Je ne connaissais pas bien le RGPD au début de ce POK et je voulais approfondir le sujet pour comprendre ensuite les procès qui ont lieu et les droits des utilisateurs. Mais aussi pour comprendre le côté légal des entreprises et leurs obligations. Je ne savais pas trop à quel point la première partie allait m'intéresser et, finalement, je me suis passionné par le sujet.

J'ai pu finir cette première partie dans les temps sans trop de soucis, mais en gardant bien le chrono à côté de moi pour ne pas me perdre sur les sujets que je voulais étudier.

{% enddetails %}

### Second Sprint

- Le règlement général sur la protection des données - RGPD. CNIL. https://www.cnil.fr/fr/reglement-europeen-protection-donnees
- Loi sur l’intelligence artificielle de l’UE - Développements et analyses actualisés de la loi sur l’intelligence artificielle de l’UE. https://artificialintelligenceact.eu/fr/
- Directive 2002/58/CE du Parlement européen et du Conseil du 12 juillet 2002 concernant le traitement des données à caractère personnel et la protection de la vie privée dans le secteur des communications électroniques (directive vie privée et communications électroniques) - Légifrance. https://www.legifrance.gouv.fr/jorf/id/JORFTEXT000000337468.
- Chambers T. L’impact du RGPD sur les entreprises internationales : enjeux et défis - Juridiques Conseils. Juridiques Conseils. https://www.avocats-valenciennes.com/limpact-du-rgpd-sur-les-entreprises-internationales-enjeux-et-defis/
- Transferts de données hors UE : le cadre général prévu par le RGPD. https://www.cnil.fr/fr/transferts-de-donnees-hors-ue-le-cadre-general-prevu-par-le-rgpd
- Novatek. Les sanctions avant et après RGPD. Novatek Consulting. https://novatek-consulting.com/les-sanctions-avant-et-apres-rgpd/. Published April 3, 2020.
- Comment se passe un contrôle de la CNIL ?  (s. d.). CNIL. https://www.cnil.fr/fr/comment-se-passe-un-controle-de-la-cnil
