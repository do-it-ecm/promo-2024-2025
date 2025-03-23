---
layout: layout/pok.njk

title: "Le RGPD "
authors:
  - Matthieu Dufort

date: 2024-12-13

temps: 3
tags:
  - "RGPD"

description: Un POK traitant du Réglement Général sur la Protection des Données, de son évolution, et de son application dans le monde du digital.
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

- [x] Etude de cas du procès de la CNIL à l'encontre de GOOGLE LLC
- [x] Etude de cas de la fuite de données récentes chez free

### Horodatage

| Date | Heures passées | Indications |
| -------- | -------- |-------- |
| dimanche 26/01 | 3H  | Origine RGPD et texte 2018 |
| lundi 27/01 | 2H  | texte et Evolution |
| mardi 28/01 | 4H  | Comparaison mondiale, Impact et controle des entreprises |
| mercredi 29/01 | 1H  | controle sur entreprise internationalle |
| mercredi 05/03 | 6H  | analyse du procès de Google LLC |
| jeudi 06/03 | 5H  | fin de l'analyse du procès de Google LLC et étude du cas Free|

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

## Adaptation des entreprises par rapport à ces différences

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

Et ceci est valable pour toutes entreprises gérant des données de citoyens européens.

{% details "Bilan Sprint 1" %}

Je ne connaissais pas bien le RGPD au début de ce POK et je voulais approfondir le sujet pour comprendre ensuite les procès qui ont lieu et les droits des utilisateurs. Mais aussi pour comprendre le côté légal des entreprises et leurs obligations. Je ne savais pas trop à quel point la première partie allait m'intéresser et, finalement, je me suis passionné par le sujet.

J'ai pu finir cette première partie dans les temps sans trop de soucis, mais en gardant bien le chrono à côté de moi pour ne pas me perdre sur les sujets que je voulais étudier.

{% enddetails %}

### Second Sprint

## Etude de cas du procès de la CNIL envers google LLC

### Contexte

Le 16 mars 2020, la CNIL lance un contrôle en ligne de certains sites des sociétés GOOGLE LLC et GOOGLE IRELAND LIMITED afin de vérifier le bon respect de l'article 82 de la loi 78-17 du RGPD.

{% details "Loi 78-17 article 82" %}

Tout abonné ou utilisateur d'un service de communications électroniques doit être informé de manière claire et complète, sauf s'il l'a été au préalable, par le responsable du traitement ou son représentant :

1° De la finalité de toute action tendant à accéder, par voie de transmission électronique, à des informations déjà stockées dans son équipement terminal de communications électroniques, ou à inscrire des informations dans cet équipement ;

2° Des moyens dont il dispose pour s'y opposer.

Ces accès ou inscriptions ne peuvent avoir lieu qu'à condition que l'abonné ou la personne utilisatrice ait exprimé, après avoir reçu cette information, son consentement qui peut résulter de paramètres appropriés de son dispositif de connexion ou de tout autre dispositif placé sous son contrôle.

Ces dispositions ne sont pas applicables si l'accès aux informations stockées dans l'équipement terminal de l'utilisateur ou l'inscription d'informations dans l'équipement terminal de l'utilisateur :

1° Soit, a pour finalité exclusive de permettre ou faciliter la communication par voie électronique ;

2° Soit, est strictement nécessaire à la fourniture d'un service de communication en ligne à la demande expresse de l'utilisateur.

{% enddetails %}

Les non-conformités concernaient essentiellement le fait qu'il n'était pas possible de refuser les cookies du site google.fr. Il y a alors eu une première injonction en 2020, qui a été clôturée en 2021 à propos :

- des finalités de tous les cookies soumis au consentement,
- des moyens dont elles disposent pour les refuser

Mais la CNIL a reçu de nouvelles plaintes et a donc rouvert une étude pour :

- Non-respect des modalités de refus des cookies

Ces longs procès sur le sujet des cookies ont duré plusieurs années avec différentes étapes résumées ci-dessous.

### Déroulement des procès

#### Première injonction

Ce procès a donc débuté avec une première délibération le 7 décembre 2020, qui a abouti aux conclusions suivantes concernant essentiellement le site google.fr :

**Extrait de LegiFrance retraçant la délibération SAN-2021-023 du 31 décembre 2021 à propos de la délibération SAN-2020-012 du 7 décembre 2020 :**

- *prononcé à l’encontre de la société [X] et de [Y] des amendes administratives d’un montant respectif de 60 millions et 40 millions d’euros pour manquement à l’article 82 de la loi Informatique et Libertés ;*
- *prononcé à l’encontre des sociétés [X] et [Y] une injonction de mettre en conformité le traitement avec les obligations résultant de l’article 82 de la loi informatique et libertés , en particulier :*
  - *informer les personnes concernées au préalable et de manière claire et complète, par exemple sur le bandeau d’information présent sur la page d’accueil du site [V].fr :*
- *des finalités de tous les cookies soumis au consentement,*
- *des moyens dont elles disposent pour les refuser ;*
- *assorti l’injonction d’une astreinte de 100 000 euros par jour de retard à l’issue d’un délai de trois mois suivant la notification de la présente délibération ;*
- *rendu publique, sur le site de la CNIL et sur le site de Légifrance, sa délibération, qui n’identifiera plus nommément les sociétés à l’expiration d’un délai de deux ans à compter de sa publication.*

Suite à cela, les deux sociétés ont fait appel à l'injonction auprès du Conseil d'État, qui a refusé leur recours.

Elles se sont alors mises en conformité en affichant dans un bandeau d'information les moyens de refuser les cookies, ainsi que toutes les informations concernant leur utilisation et leur finalité. Cette conformité a été validée par la CNIL, mettant ainsi fin à cette première injonction.

#### Seconde injonction

Mais la CNIL reçoit ensuite des plaintes concernant les modalités de refus des cookies sur google.fr et youtube.com. En juin 2021, un nouveau contrôle en ligne est effectué. Cela aboutit à une nouvelle amende, toujours en lien avec l'article 82 du RGPD.

Cependant, le premier procès étant encore en recours auprès du Conseil d'État, les entreprises demandent une pause dans ce second procès, estimant que la réponse du premier pourrait impacter le second. Elles invoquent également le principe du non bis in idem, car elles dénoncent le fait de se voir accuser deux fois pour la même chose. Cette demande est refusée, car le premier procès portait sur la connaissance des finalités de tous les cookies soumis au consentement ainsi que sur les moyens de les refuser, tandis que le second concerne spécifiquement les modalités de refus des cookies (qui doivent être aussi simples que leur acceptation). Il s'agit donc de deux cas différents.

Ces deux procès étant étroitement liés, les sociétés ont largement joué sur cette connexion dans l'espoir de sortir de ces accusations.

La CNIL poursuit ses investigations avec un contrôle sur l'utilisation des cookies, en s'appuyant sur la directive ePrivacy, article 5, paragraphe 3, en lien avec l'article 82 du RGPD. Elle conclut que l'utilisation et le stockage des cookies ne sont pas conformes. Cette directive permet également d'éviter de passer par la règle du guichet unique du RGPD, qui aurait dû transférer ce contrôle à l'autorité de contrôle irlandaise, étant le guichet unique de Google.

{% details "Article 5 de la directive ePrivacy" %}

Confidentialité des communications

1. Les États membres garantissent, par la législation nationale, la confidentialité des communications effectuées au moyen d'un réseau public de communications et de services de communications électroniques accessibles au public, ainsi que la confidentialité des données relatives au trafic y afférentes. En particulier, ils interdisent à toute autre personne que les utilisateurs d'écouter, d'intercepter, de stocker les communications et les données relatives au trafic y afférentes, ou de les soumettre à tout autre moyen d'interception ou de surveillance, sans le consentement des utilisateurs concernés sauf lorsque cette personne y est légalement autorisée, conformément à l'article 15, paragraphe 1. Le présent paragraphe n'empêche pas le stockage technique nécessaire à l'acheminement d'une communication, sans préjudice du principe de confidentialité.

2. Le paragraphe 1 n'affecte pas l'enregistrement légalement autorisé de communications et des données relatives au trafic y afférentes, lorsqu'il est effectué dans le cadre des usages professionnels licites, afin de fournir la preuve d'une transaction commerciale ou de toute autre communication commerciale.

3. Les États membres garantissent que l'utilisation des réseaux de communications électroniques en vue de stocker des informations ou d'accéder à des informations stockées dans l'équipement terminal d'un abonné ou d'un utilisateur ne soit permise qu'à condition que l'abonné ou l'utilisateur, soit muni, dans le respect de la directive 95/46/CE, d'une information claire et complète, entre autres sur les finalités du traitement, et que l'abonné ou l'utilisateur ait le droit de refuser un tel traitement par le responsable du traitement des données. Cette disposition ne fait pas obstacle à un stockage ou à un accès techniques visant exclusivement à effectuer ou à faciliter la transmission d'une communication par la voie d'un réseau de communications électroniques, ou strictement nécessaires à la fourniture d'un service de la société de l'information expressément demandé par l'abonné ou l'utilisateur.

{% enddetails %}

{% details "Principe du Guichet Unique du RGPD" %}

Un mécanisme ouvert aux seules entreprises établies en UE : lorsqu’une entreprise met en œuvre un traitement de données « transfrontalier », elle bénéficie d’un mécanisme de contrôle simplifié. Celui-ci ne s’applique pas aux entreprises exclusivement établies hors de l’UE.
Un interlocuteur unique pour les responsables de ces traitements : il s’agit de l’autorité « chef de file », c’est-à-dire l’autorité de protection des données du pays où se trouve l’établissement principal de l’entreprise. C’est auprès de cette seule autorité que les différentes obligations prévues par le RGPD doivent être accomplies. Elle est en outre chargée de coordonner la prise de décision avec les autres autorités de protection des données concernées par le traitement transfrontalier.
Une seule décision valable dans toute l’UE : toute décision de l’autorité chef de file aura été prise en concertation avec l’ensemble des autorités de protection des données concernées. Elle présentera donc l’interprétation commune des autorités européennes concernant le traitement transfrontalier à l’égard duquel la décision est prise.

{% enddetails %}

L'injonction a alors lieux et la formation de la CNIL délivre les sanctions suivantes :

**Extrait de LegiFrance retraçant la Délibération SAN-2021-023 du 31 décembre 2021 :**

- *prononcer à l’encontre de la société [X] une amende administrative d’un montant de 90 000 000 euros (quatre-vingt-dix millions d’euros) pour manquement à l’article 82 de la loi Informatique et Libertés ,*
- *prononcer à l’encontre de la société [Y] une amende administrative d’un montant de 60 000 000 euros (soixante millions d’euros) pour manquement à l’article 82 de la loi Informatique et Libertés,*
- *prononcer à l’encontre des sociétés [X] et [Y] une injonction de modifier, sur les sites web [V].fr et [W].com , les modalités de recueil du consentement des utilisateurs situés en France aux opérations de lecture et/ou d’écriture d’informations dans leur terminal, en leur offrant un moyen de refuser ces opérations présentant une simplicité équivalente au mécanisme prévu pour leur acceptation, afin de garantir la liberté de leur consentement ;*
- *assortir l’injonction d’une astreinte de 100 000 euros (cent mille euros) par jour de retard à l’issue d’un délai de trois mois suivant la notification de la présente délibération, les justificatifs de la mise en conformité devant être adressés à la formation restreinte dans ce délai ;*
- *adresser cette décision à la société [Z] en vue de son exécution ;*
- *rendre publique, sur le site de la CNIL et sur le site de Légifrance, sa délibération, qui n’identifiera plus nommément les sociétés à l’expiration d’un délai de deux ans à compter de sa publication.*

Cette injonction a ensuite été cloturé en juillet 2023 suite à la réaction de Google dans le temps imparti des 3 mois pour mettre en place un bouton *Tout refuser* à coté de celui *Tout accepter*.

### Conséquences de ces injonctions

Tout d'abord, on peut observer que même si ces injonctions et procès prennent du temps, ils sont efficaces, car finalement les sociétés accusées ont bien modifié leur site pour se mettre en conformité.

Cependant, ce n'est pas la première fois que Google est sanctionné en Europe. En 2021, c'est un total de 2,5 milliards d'euros d'amende pour manipulation de données (avec le comparateur Google Shopping) et le refus des cookies. Mais, avec un chiffre d'affaires de 300 milliards de dollars en 2024 et 100 milliards de bénéfice, on peut se demander si ces amendes sont suffisantes pour vraiment dissuader. Après Google, c'est Facebook qui a été sanctionné pour des manquements à la loi Informatique et Libertés, avec une amende de 390 millions d'euros, puis à nouveau de 1,2 milliard. Il semble donc que tous ces géants du web ne semblent pas vraiment être dissuadés.

## Etude de cas, la fuite de données de Free

### Contexte

Fin octobre 2024, l'opérateur Free a subi une cyberattaque qui a entraîné une fuite de données de 19 millions de comptes. Dans les données volées, il y a des noms, des prénoms, des adresses ainsi que des numéros de téléphone d'abonnés. Il y a aussi 5 millions d'IBAN, ce qui fait craindre des tentatives d'arnaques bancaires à venir. Suite à cela, Free a prévenu la CNIL et le gouvernement a alors publié un [article](https://www.cybermalveillance.gouv.fr/tous-nos-contenus/actualites/violation-de-donnees-personnelles-free-202410) afin d'avertir les utilisateurs. Il rappelle aussi qu'il est possible de porter plainte en cas d'utilisation frauduleuse de ses données, mais aussi si l'on considère que ses données personnelles ont mal été protégées.

### Risque judiciaire pour l'entreprise

Ainsi, l'entreprise est bien sûr en danger judiciairement. Cependant, elle n'est pas forcément tenue coupable. En effet, malheureusement, étant donné qu'aucun pare-feu n'est inviolable, une fuite de données peut être possible. Mais l'entreprise doit avoir fait le maximum pour protéger les données. Ainsi, elle ne peut être coupable que si la CNIL découvre un manquement en matière de cybersécurité.

Elle peut aussi être accusée en cas de mauvaise réaction face à cette fuite. Si la fuite avait été cachée de la CNIL pendant plus de 72 heures, comme le stipule l'article 33 du RGPD, elle aurait pu être accusée. De même, elle peut être accusée si elle ne prévient pas chaque utilisateur dont les données ont fuité, en particulier lorsqu'il s'agit de données sensibles, comme énoncé dans l'article 34.

{% details "Article 33 : Notification à l'autorité de contrôle d'une violation de données à caractère personnel" %}

En cas de violation de données à caractère personnel, le responsable du traitement en notifie la violation en question à l'autorité de contrôle compétente conformément à l'article 55, dans les meilleurs délais et, si possible, 72 heures au plus tard après en avoir pris connaissance, à moins que la violation en question ne soit pas susceptible d'engendrer un risque pour les droits et libertés des personnes physiques. Lorsque la notification à l'autorité de contrôle n'a pas lieu dans les 72 heures, elle est accompagnée des motifs du retard.

Le sous-traitant notifie au responsable du traitement toute violation de données à caractère personnel dans les meilleurs délais après en avoir pris connaissance.

La notification visée au paragraphe 1 doit, à tout le moins:

- a) décrire la nature de la violation de données à caractère personnel y compris, si possible, les catégories et le nombre approximatif de personnes concernées par la violation et les catégories et le nombre approximatif d'enregistrements de données à caractère personnel concernés;
- b) communiquer le nom et les coordonnées du délégué à la protection des données ou d'un autre point de contact auprès duquel des informations supplémentaires peuvent être obtenues;

- c) décrire les conséquences probables de la violation de données à caractère personnel;

- d) décrire les mesures prises ou que le responsable du traitement propose de prendre pour remédier à la violation de données à caractère personnel, y compris, le cas échéant, les mesures pour en atténuer les éventuelles conséquences négatives.

Si, et dans la mesure où, il n'est pas possible de fournir toutes les informations en même temps, les informations peuvent être communiquées de manière échelonnée sans autre retard indu.

Le responsable du traitement documente toute violation de données à caractère personnel, en indiquant les faits concernant la violation des données à caractère personnel, ses effets et les mesures prises pour y remédier. La documentation ainsi constituée permet à l'autorité de contrôle de vérifier le respect du présent article.

{% enddetails %}

{% details "Article 34 : Communication à la personne concernée d'une violation de données à caractère personnel" %}

Lorsqu'une violation de données à caractère personnel est susceptible d'engendrer un risque élevé pour les droits et libertés d'une personne physique, le responsable du traitement communique la violation de données à caractère personnel à la personne concernée dans les meilleurs délais.

La communication à la personne concernée visée au paragraphe 1 du présent article décrit, en des termes clairs et simples, la nature de la violation de données à caractère personnel et contient au moins les informations et mesures visées à l'article 33, paragraphe 3, points b), c) et d).

La communication à la personne concernée visée au paragraphe 1 n'est pas nécessaire si l'une ou l'autre des conditions suivantes est remplie:

- a) le responsable du traitement a mis en œuvre les mesures de protection techniques et organisationnelles appropriées et ces mesures ont été appliquées aux données à caractère personnel affectées par ladite violation, en particulier les mesures qui rendent les données à caractère personnel incompréhensibles pour toute personne qui n'est pas autorisée à y avoir accès, telles que le chiffrement;
- b) le responsable du traitement a pris des mesures ultérieures qui garantissent que le risque élevé pour les droits et libertés des personnes concernées visé au paragraphe 1 n'est plus susceptible de se matérialiser;
- c) elle exigerait des efforts disproportionnés. Dans ce cas, il est plutôt procédé à une communication publique ou à une mesure similaire permettant aux personnes concernées d'être informées de manière tout aussi efficace.

Si le responsable du traitement n'a pas déjà communiqué à la personne concernée la violation de données à caractère personnel la concernant, l'autorité de contrôle peut, après avoir examiné si cette violation de données à caractère personnel est susceptible d'engendrer un risque élevé, exiger du responsable du traitement qu'il procède à cette communication ou décider que l'une ou l'autre des conditions visées au paragraphe 3 est remplie.

{% enddetails %}

### La suite de l'histoire sur cette fuite de données

Cette fuite de données a une histoire légèrement particulière qui n'est d'ailleurs toujours pas vraiment résolue.

Les données ont été mises aux enchères à un prix initial de 70 000 dollars, avec une menace envers l'entreprise expliquant que si Free ne gagnait pas la vente, cela rendrait les données probablement publiques sur un forum. Puis, une annonce est faite, la base est vendue pour 175 000 dollars. Quelques jours plus tard, les messages sont supprimés et plus aucune nouvelle du hacker.

Un autre pirate tente alors de vendre 4 autres versions pour 35 000 dollars en annonçant que le premier a été arrêté, mais l'hypothèse principale est un SCAM de ce pirate.

En novembre, un autre pirate entre dans l’action pour dire qu’il était le pirate et qu’aucune des données n’a été vendue. Il affirme avoir fait cela uniquement pour informer les Français de la surveillance de masse. Ce pirate aurait déjà alerté Free suite à sa condamnation par la CNIL en 2022, mais aurait été ignoré. Il affirme aujourd’hui ne pas savoir ce qu'il va faire des données (les détruire, vendre, etc.). L'avenir nous le dira !

{% details "Bilan Sprint 1" %}

J'ai pris beaucoup de plaisir à travailler sur ce deuxième sprint car les histoires sur ces procès sont très intéressantes. Les entreprises utilisent énormément d'arguments pour tenter de continuer leur activité et éviter les sanctions, tandis que la CNIL tente de modifier les choses. Elles font alors appel à beaucoup d'articles et de lois, ce qui rend la chose un peu difficile à suivre par moments. J'ai ainsi pris plus de temps car, pour comprendre un argument, j'ai parfois dû y passer près d'une heure. Cependant, je trouve toute cette partie régulation très intéressante et j'ai beaucoup apprécié suivre le procès tout en me plongeant dans des articles de lois.

Le cas de Free est allé un peu plus vite que prévu (heureusement vu la complexité de celui de Google), mais il m'a permis de bien découvrir les risques d'une fuite de données pour une entreprise judiciairement.

À certains moments, on a l'impression de se retrouver dans la série *Suits* en lisant le déroulé des procès et les rebondissements. Et, ayant beaucoup apprécié cette série, j'ai bien apprécié ce POK !

{% enddetails %}


## Bibliographie

### Sprint 1

- Le règlement général sur la protection des données - RGPD. [CNIL](https://www.cnil.fr/fr/reglement-europeen-protection-donnees)
- Loi sur l’intelligence artificielle de l’UE - Développements et analyses actualisés de la loi sur l’intelligence artificielle de l’[UE](https://artificialintelligenceact.eu/fr/)
- Directive 2002/58/CE du Parlement européen et du Conseil du 12 juillet 2002 concernant le traitement des données à caractère personnel et la protection de la vie privée dans le secteur des communications électroniques (directive vie privée et communications électroniques) - [Légifrance](https://www.legifrance.gouv.fr/jorf/id/JORFTEXT000000337468)
- Chambers T. L’impact du RGPD sur les entreprises internationales : enjeux et défis - Juridiques Conseils. [Juridiques Conseils](https://www.avocats-valenciennes.com/limpact-du-rgpd-sur-les-entreprises-internationales-enjeux-et-defis/)
- Transferts de données hors UE : le cadre général prévu par le RGPD. [CNIL](https://www.cnil.fr/fr/transferts-de-donnees-hors-ue-le-cadre-general-prevu-par-le-rgpd)
- Novatek. Les sanctions avant et après RGPD. [Novatek Consulting](https://novatek-consulting.com/les-sanctions-avant-et-apres-rgpd/), Published April 3, 2020.
- Comment se passe un contrôle de la CNIL ?  (s. d.). [CNIL](https://www.cnil.fr/fr/comment-se-passe-un-controle-de-la-cnil)

### Sprint 2

- Clôture de l’injonction prononcée à l’encontre de GOOGLE. [CNIL](https://www.cnil.fr/fr/cloture-de-linjonction-prononcee-lencontre-de-google-0)
- Délibération SAN-2021-023 du 31 décembre 2021 - [Légifrance](https://www.legifrance.gouv.fr/cnil/id/CNILTEXT000044840062).
- Le guichet unique. [CNIL](https://www.cnil.fr/fr/le-guichet-unique)
- Gavois S. Fuite chez Free : la folle histoire des données vendues… ou pas. [Next](https://next.ink/156902/fuite-chez-free-les-donnees-nont-jamais-ete-vendues-aux-encheres-et-ne-vont-pas-letre/) Published November 6, 2024.