---
layout: layout/mon.njk

title: "Systèmes d'information de la donnée produit"
authors:
  - Esther Henry

date: 1971-03-01
temps : 3
tags: 
  - "SI"
  - "Donnée produit"
  - "PIM"
  - "PLM"


résumé: "L’objectif de ce MON est de mieux comprendre l’environnement des outils de gestion de la donnée produit, de type PIM, DAM, PLM, MDM..."
---

{% prerequis %}

Notion de base sur les systèmes d’information

{% endprerequis %}

## Contexte

Dans le cadre de mon alternance, je travaille sur un projet de système d’information autour de la donnée produit. Cependant, c’est un sujet assez tentaculaire et il existe différentes grandes catégories de SI de ce type, que je ne connais pas suffisamment, ce qui limite ma compréhension du projet. J’aimerais donc profiter de ces 10h pour approfondir le sujet, notamment en me renseignant sur ces SI, à savoir à ma connaissance : **PIM, PLM, DAM, MDM, ETL**, et peut-être d’autres que j’ignore.

L’objectif pour moi est de mieux maîtriser les spécificités de chacun de ces outils pour mieux **comprendre l’organisation d’un système d’information organisé autour de la donnée produit**.

## Définition de ces différents types de SI

Avec tous ces acronymes qui peuvent être confusants, un point définition s’impose.  

En théorie, ces solutions couvrent des besoins différents, mais en pratique, certaines fonctionnalités se recoupent ou sont hybrides. Il faut donc faire attention au côté marketing des éditeurs, qui peuvent vendre des solutions sous de beaux noms tendance sans réellement répondre à leurs véritables fonctionnalités.

### PIM

#### Défintion d’un PIM

Un PIM, pour *Product Information Management* (ou en français *Gestion d’information sur les produits*), est un outil qui décrit les produits par des attributs organisés. C’est un SI structuré autour de la donnée produit ; on peut le voir en quelque sorte comme un catalogue de produits.  

Les objectifs principaux d’un PIM sont les suivants : **collecter, centraliser, enrichir et publier les informations produits**.  

La spécificité d’un PIM réside notamment dans le fait que les données sont **regroupées par référence de produit**, ce qui n’est pas forcément le cas des autres systèmes d’information. On parle alors de **données structurées**.

#### A quoi sert un PIM ?

Un PIM sert notamment à développer et suivre la **stratégie marketing**, car il centralise toutes les informations relatives aux produits, y compris celles destinées aux clients. Un PIM a donc aussi pour fonction de contenir les informations permettant d’informer les **canaux de vente et de distribution** des produits. Plus loin encore, on peut dire qu’il relie les données des canaux de fabrication à ceux de distribution.  

Ici, la donnée peut être communiquée et diffusée de manière informatique ou sur papier. En effet, des solutions spécifiques pour ces deux cas permettent de produire des fiches produits très particulières en fonction du besoin. On peut donc dire que le PIM est plutôt un outil à destination des besoins externes de l’entreprise, c'est-à-dire des consommateurs ou des clients.  

Une autre utilité du PIM est de garantir la cohérence de **l’image de marque** en centralisant les informations essentielles à celle-ci.  

Un aspect supplémentaire qui peut être pris en charge par un outil PIM est la gestion des **traductions dans les environnements multilingues**. Ainsi, le PIM permet de gérer les informations dans diverses langues.  

Par ailleurs, on peut noter que le PIM est un outil majoritairement destiné à une utilisation par les métiers et qu’il a donc en général une **UI friendly**, ce qui n’est pas le cas de tous les SI en entreprise.

#### Avantages possible du PIM

Grâce à l’implémentation d’un PIM dans son système d’information, une entreprise peut espérer :  

- Améliorer sa **gestion**, son **maintien** et la **qualité de sa donnée produit**
- **Diminuer les coûts** grâce à la centralisation des informations qu’il permet
- **Augmenter la rapidité de communication**

#### Métiers qui utilisent un PIM

Parmi les principaux métiers utilisateurs du PIM en entreprise, on retrouve :  

- **Marketing**  
- **Communication**  
- **Marketing digital**  
- **Logistique**  
- **Réglementaire** (souvent pour les étapes de validation)  
- **Achat / Commerciaux** (utilisent la donnée mais n’en saisissent pas en général)  

#### Ce que n’est pas un PIM

- **ERP** (pas de gestion des factures)  
- **CRM** (pas de gestion des données clients)  
- **PLM** (pas de gestion des données liées à la création du produit, type R&D)  
- **E-commerce** (pas de ventes directes)  

{% attention %}  
En revanche, l’ERP et le PLM peuvent être des sources de données dans le PIM. Il est donc possible d'interfacer un PIM avec ces différentes solutions pour permettre la sollicitation de ces données si besoin.  
{% endattention %}  

### PLM

#### Défintion d’un PLM

Un PLM, pour *Product Lifecycle Management* (ou gestion du cycle de vie du produit en français), est un acronyme utilisé à la fois pour désigner des méthodes et des logiciels. Historiquement, le PLM est une méthode de gestion, puis avec l’arrivée du numérique, des logiciels de PLM se sont développés.  

Le PLM permet de gérer et d’optimiser le processus des données tout au long du **cycle de vie du produit**, de la description de son cahier des charges à sa fin de vie.  

L’objectif est que le PLM soit une source de données unique et robuste, ce qu’on appelle : la **single source of truth**.  

Comme pour le PIM, pour le PLM, on parle de données structurées.

#### A quoi sert un PLM ?

Le PLM va répondre aux besoins suivants :  

- Définition du cahier des charges du produit ou des exigences marketing  
- Détail de la conception du produit  
- Les nomenclatures produit  
- Gestion de la fabrication du produit  
- Gestion des exigences (réglementaires)  
- Gestion des projets  
- Gestion de la mise sur le marché du produit  
- Gestion de la distribution du produit  
- Gestion des modifications  
- Gestion de la fin de vie du produit (déchets, recyclage, ...)  

Dans le contexte de SI autour du produit, le **PLM se situe en amont du PIM**, avec les données, notamment des fournisseurs.  

Le PLM se focalise sur le développement et la **connaissance fine du produit**, que ce soit ses matières, ses origines, ses recettes, son histoire, de l’innovation en R&D à son industrialisation. Le PLM intègre aussi des **processus métier** comme la formulation, le développement de packaging, ou les audits, par exemple.  

Le PLM va aussi permettre une meilleure gestion des connaissances acquises : en centralisant l’information, on a un **historique** de ce qui a déjà été fait et donc on peut s’en servir pour les développements ou projets futurs.  

Ainsi, le PLM permet de regrouper un grand nombre de fonctions qui peuvent historiquement être sillonnées dans un grand nombre de SI différents, que l’on aurait implémentés successivement au fil des besoins, pour chaque fonctionnalité que le PLM va permettre de regrouper. Souvent, le passage au PLM se fait quand les entreprises atteignent **les limites de ce système de silos**, car une multitude de sources de données implique des erreurs et peu de gouvernance des données.  

Ainsi, le développement ou la mise en place du PLM est un gros enjeu pour le modèle de données et de nomenclatures à mettre en place.

#### Avantages possible du PLM

Lorsqu’une entreprise met en place un PLM, elle peut espérer en tirer les avantages suivants :  

- Réduire le délai de mise sur le marché  
- Améliorer la qualité du produit  
- Réduire les coûts de prototypes  
- Réduire les déchets  
- Garantir la prise de bonnes décisions  
- Limiter la ressaisie et les pertes de temps liées à la recherche d’information  
- Stopper la segmentation en silos, ce qui facilite la communication entre équipes  
- Garantir la validité des données  
- Sécuriser et assurer la traçabilité des données  
- Faciliter la standardisation des processus de conception  

#### Métiers qui utilisent un PLM

Voici la liste des principaux métiers utilisateurs d’un PLM en entreprise :  

- **R&D**  
- **Projet**  
- **Réglementaires**  
- **Achat**  
- **ADV**  
- **Marketing** (lecteur plutôt qu'éditeur)  

### DAM

#### Définition du DAM

Un DAM pour **Data Asset Management** ou en français **gestion des actifs numériques**, sert à **stocker des documents de toutes sortes** (bureautiques, PDF, Word, image, …) ainsi que leurs **métadonnées**, avec notamment des fonctionnalités de workflow, de recherche, ainsi qu’une historisation des actions plus ou moins élaborée selon les solutions. L’association des médias avec ces métadonnées permet de faciliter l’utilisation du média et son référencement.

En comparaison à la GED que nous verrons ci-dessous, le DAM a la particularité d’être **spécialiste des médias** (images, vidéos, sons, …).

Le DAM change la manière d’utiliser ces médias, car il permet une **source unique de médias**, limitant ainsi l’espace de stockage. Grâce aux outils qu’il propose, il permet d’optimiser la mise en valeur des médias, notamment à destination de ses clients (B2B ou B2C). Les solutions DAM deviennent notamment indispensables dans les entreprises dès qu'elles doivent **gérer un nombre élevé de médias**.

Le développement rapide des solutions DAM a été lié à un besoin croissant dû à un changement dans le marketing des produits. En effet, les entreprises cherchent de plus en plus à faire des **publicités ciblées**, mais aussi sur un nombre de **canaux** toujours plus important (mails, papier, réseaux sociaux, médias traditionnels …).

L’importance de **l’image de marque** a aussi accéléré l’implémentation des DAM, car pour avoir une image de marque impeccable, il faut s’assurer de la clarté de l’organisation de ces médias (logo, images, charte graphique).

À l’inverse des PIM et PLM, pour le DAM, on parle de données peu ou pas structurées.

#### A quoi sert un DAM ?

Un DAM peut regrouper plus ou moins de fonctions, selon ses modules. On retrouve :  

**Fonctions de base :**  

- Alimentation
- Annotation  
- Classement  
- Stockage  
- Recherche  

**Fonctions supplémentaires :**  

- Fonction de détourage
- Gestion des tags  
- Détection d’image  
- Notion de téléchargement  
- Renommage  
- Sauvegarde  
- Regroupement  
- Archivage  
- Optimisation  
- Entretien  
- Compression  
- Exportation de fichiers numériques  

Par ailleurs, dans certains cas, le **DAM est directement intégré au PIM**, ce sont des solutions très souvent complémentaires.

#### Avantages possible du DAM

En choisissant d’utiliser un DAM pour ses assets numériques, une entreprise peut espérer les avantages suivants :  

- Gain de temps  
- Réduction de la duplication des fichiers  
- Amélioration de la cohérence de marque  
- Optimisation des processus de création  
- Sécurisation et contrôle des accès  
- Réduction des coûts  
- Compatibilité multicanale  
- Suivi et analytics  
- Conformité et archivage  

#### Métiers qui utilisent un DAM

En entreprise, les principaux métiers qui utilisent le DAM sont les suivants :  

- Marketing  
- Marketing digital  
- Communication  
- Création (studio, design)  

### GED

#### A quoi sert une GED?

{% info %}

Nous ne rentrerons pas beaucoup dans le détail pour la GED car ce n’est pas le sujet principal, mais il est important de l’aborder car elle est présente dans la plupart des entreprises pour des questions réglementaires, et qu’il est important de comprendre ses différences vis-à-vis du DAM.

{% endinfo %}

Une GED, pour Gestion Électronique des Documents, sert à gérer le stockage et l’archivage des documents (notamment réglementaires des entreprises).

Comme le DAM, la GED sert à **stocker des documents de toutes sortes** (bureautique, PDF, Word, image, …) ainsi que leurs métadonnées, avec des fonctionnalités de workflow, de recherche, et une historisation des actions, plus ou moins élaborée selon les solutions.

Mais contrairement au DAM, qui est spécialiste des médias, le point fort de la GED est sa capacité à stocker des **documents pour le métier** (par exemple, la qualité) et en faire des **recherches poussées**. Par exemple, on peut retrouver des éléments d’analyse bactériologiques, qui sont gérés comme des pièces jointes.

Comme pour le DAM, on parle de données peu ou pas structurées.

### MDM

#### A quoi sert un MDM?

Un MDM pour Master Data Management, ou en français gestion des données de référence ou gestion des données maîtres, réunit les **données de référence** de l’entreprise en se centrant sur un attribut qui peut être le produit, mais pas forcément. On peut aussi avoir un MDM basé sur : fournisseur, client, canaux de distribution, tarif, et il est aussi possible de le centrer sur des attributs cumulés (multiréférentiel). 

Souvent, le MDM est mis en place dans une volonté de **gouvernance de la donnée** au sein de l’entreprise. Contrairement à un PIM, le MDM répond aux besoins internes de l’entreprise, avec notamment ses **données stratégiques**.

En effet, ce sont des données qu’il est nécessaire d’agréger pour fournir une **information unique et contextualisée**, ce qui est indispensable pour créer un **langage commun**, permettant ainsi de faire du **décisionnel** en entreprise.

#### Avantages possible du MDM

Les entreprises mettant en place un MDM peuvent espérer en tirer les avantages suivants :

- Création d’une source unique de vérité (Single Source of Truth)
- Création d’un langage commun
- Réduction des erreurs et incohérences
- Meilleure prise de décision
- Optimisation des processus métier
- Réduction des coûts liés aux erreurs de données
- Renforcement de la conformité et de la gouvernance des données

#### Métiers qui utilisent un MDM

Les métiers qui utilisent le plus le MDM en entreprises sont :

- IT
- Projet SI
- Data analyst
- BI
- Direction (prise de décision)

### ETL  

#### Définition d’un ETL

Un ETL pour **Extract, Transform, Load**, extraction, transformation et chargement en français, est un processus ou un outil permettant d’extraire des données depuis différentes sources, de les transformer en un format exploitable, puis de les charger dans un système cible (data warehouse, base de données, …). Il joue un rôle clé dans l'intégration et la consolidation des données pour l'analyse et la prise de décision.

L’ETL est une partie essentielle des architectures **décisionnelles** et **Big Data**, assurant la qualité, la cohérence et l’accessibilité des données.

#### À quoi sert un ETL ?

L’ETL permet de répondre aux besoins suivants :  

- Extraction des données depuis des sources hétérogènes (ERP, CRM, API, fichiers plats...) 
- Nettoyage et transformations : correction des erreurs, harmonisation des formats, enrichissement des données
- Chargement dans un système cible (data warehouse, datamart, base analytique) 
- Automatisation des flux de données 
- Amélioration de la qualité et de la gouvernance des données en centralisant et structurant l'information.  

Dans une architecture SI, **l’ETL intervient avant l’analyse des données**, en s'assurant que les informations sont prêtes pour être exploitées dans des outils de reporting ou d’intelligence artificielle.

#### Avantages possibles de l’ETL

L’implémentation d’un ETL peut apporter plusieurs bénéfices :  

- Réduction des erreurs humaines grâce à l’automatisation des processus d’intégration
- Amélioration de la qualité des données par des contrôles et des transformations adaptées  
- Gain de temps (en évitant la saisie manuelle)
- Meilleure prise de décision
- Scalabilité (pour traiter de grands volumes de données en temps réel ou différé)
- Interopérabilité avec divers systèmes d’information, ce qui facilite l'intégration et l'exploitation des données

#### Métiers qui utilisent un ETL

Les ETL sont principalement utilisés par les métiers suivants :  

- Data Engineers
- Data analysts
- BI
- Développeurs SI
- Direction IT

### Datamart

#### Définition d’un Datamart

Un **Datamart** est un sous-ensemble d’un **Data Warehouse** qui est conçu pour répondre aux besoins spécifiques d’un département ou d’un métier. Contrairement à un **Data Warehouse** qui centralise toutes les données de l’entreprise, un Datamart se concentre sur un domaine particulier, permettant un accès rapide et ciblé aux données (par exemple aux données produits, mais pas que).  

Il sert de point d’accès simplifié pour les utilisateurs métier, en structurant les informations de manière optimisée pour l’analyse et l’aide à la décision. Le datamart ne va pas obtenir toutes les informations, mais seulement un extrait de celles-ci spécifiques aux besoins de tel ou tel métier.

#### À quoi sert un Datamart ?  

Un **Datamart** permet de :  

- Centraliser les données métier car il regroupe les informations utiles à un département spécifique  
- Accélérer l’analyse et la prise de décision en améliorant la performance des requêtes grâce à une structure adaptée aux besoins des utilisateurs  
- Réduire la complexité en simplifiant l’accès aux données par rapport à un Data Warehouse plus global en retirant les données inutiles  
- Faciliter l’intégration avec des outils analytiques en alimentant les tableaux de bord et rapports spécifiques.  

Dans une architecture SI, le Datamart est souvent **alimenté par un Data Warehouse**, mais peut aussi être autonome et relié directement à différentes sources de données comme un ERP par exemple.

#### Avantages possibles d’un Datamart

L’implémentation d’un Datamart peut offrir les bénéfices suivants aux entreprises :

- Meilleure performance des requêtes analytiques  
- Simplification de l’accès aux données pour les équipes métier  
- Réduction des coûts liés à l’exploitation d’un Data Warehouse complet  
- Gain en autonomie des utilisateurs grâce à une structure adaptée  
- Sécurisation et gouvernance des données en fonction des besoins métier  
- Amélioration de la prise de décision avec des analyses plus rapides et précises

#### Métiers qui utilisent un Datamart

Les principaux utilisateurs d’un Datamart sont :  

- Marketing  
- Finance  
- Ressources Humaines  
- Supply Chain  
- Ou tout métier pour lequel on aurait développé un Datamart spécifique  
- Direction

## Tableau comparatif de ces SI produit

| **Système**               | **Objectif principal**                                       | **Type de données gérées**                                   | **Bénéfices**                                      | **Limites**                                      | **Utilisateurs principaux**                           | **Exemples d’outils**                                      |
|---------------------------|-------------------------------------------------------------|-------------------------------------------------------------|----------------------------------------------------|--------------------------------------------------|---------------------------------------------------|----------------------------------------------------------|
| **PIM** (Product Information Management) | Centralisation et diffusion des données produits            | Descriptions, attributs, médias produits                   | Cohérence et diffusion multicanal               | Gestion limitée du cycle de vie                | Marketing, e-commerce, distribution             | Akeneo, InRiver, Salsify                               |
| **PLM** (Product Lifecycle Management)  | Gestion du cycle de vie des produits                       | Données techniques, nomenclatures, versions                | Meilleure collaboration en R&D                  | Complexité et coût de mise en place              | R&D, ingénierie, production                     | Windchill, Teamcenter, Enovia                        |
| **DAM** (Digital Asset Management)      | Gestion des assets numériques                             | Images, vidéos, documents marketing                        | Réduction des duplications de fichiers            | Pas de gestion des données métier                | Communication, marketing                        | Adobe Experience Manager, Bynder                   |
| **MDM** (Master Data Management)        | Centralisation des données de référence                   | Données de référence (clients, fournisseurs, produits)     | Vision unique des données stratégiques           | Mise en œuvre longue et complexe                | IT, gouvernance des données                     | Informatica MDM, SAP MDG, Reltio                   |
| **GED** (Gestion Électronique de Documents) | Gestion et archivage des documents                        | Documents bureautiques, contrats, procédures              | Structuration et accès facilité aux documents   | Recherche parfois limitée selon les formats     | Tous services                                   | SharePoint, OpenText, Alfresco                     |
| **ETL** (Extract, Transform, Load)      | Extraction, transformation et chargement des données      | Données brutes et transformées                            | Automatisation et intégration des flux de données | Peut nécessiter des compétences techniques avancées | IT, Data Engineers                             | Talend, Apache Nifi, Informatica PowerCenter        |
| **Datamart**                             | Stockage et analyse de données métier                     | Données analytiques sectorielles                           | Accélération des analyses décisionnelles         | Données partielles et limitées à un domaine spécifique | Analystes, décideurs métier                     | Amazon Redshift, Snowflake, Google BigQuery        |

## Enjeux de l’implémentation de ces SI

### Choisir la bonne solution

Le risque avec tous ces acronymes pour des fonctionnalités différentes, c’est de se perdre dans une multitude de solutions et d’éditeurs, et de ne pas savoir qui choisir, ou de faire un mauvais choix.

Pour éviter cela, il est préférable de faire appel à des experts pour être accompagné dans ces démarches (bien fixer ses besoins et trouver une solution adaptée).

### Interfaçage

Dans de nombreuses entreprises, le système d’information est complexe et regroupe de nombreux outils et solutions qui, dans le pire des cas, ont été développés de manière indépendante et silotée, ce qui n’est franchement pas recommandé, mais malheureusement existe.

Ainsi, un des enjeux de ces SI orientés produit est l’interfaçage entre les différentes solutions. Par exemple, si l’entreprise possède déjà un PIM et un ERP et qu’elle veut mettre en place un PLM, elle devra s’assurer qu’il est possible de créer des interfaces avec ces solutions existantes et la solution PLM choisie, car le but est de réduire les silos, ce qui ne sera pas possible sans interface.

### Sécurité

Enjeux de la sécurité des données : par exemple, dans un PLM, on va pouvoir stocker des données confidentielles (mode de production, brevets, …) qui ne doivent pas être diffusées à n’importe qui. Dans le cas d’une interface entre le PLM et le PIM, il faudra donc être vigilant à quelle information circule, car les utilisateurs du PIM ne sont pas les mêmes que ceux du PLM et ne doivent donc pas, pour certains, avoir accès à ces données.  

Il y a donc, dans les SI autour de la donnée produit, un enjeu très fort de sécurité des données.

### Sobrieté numérique

Le DAM fait partie des enjeux forts de sobriété numérique dans cet environnement des SI produits, car par exemple, 80% du poids d’un site web est dû à ces médias (photos et vidéos) et récemment, il y a une grosse tendance à mettre des vidéos sur les sites produits.  
Il est donc possible de réduire l'impact carbone en optimisant sa gestion de médias.  

**Éco-conception** : enjeux à prendre en compte dès la conception du SI.  
Solutions développées pour être optimales (pas de perte inutile) et, par la suite, démarche d’amélioration continue à mettre en place.

**Source de données unique** : permet de centraliser et donc de ne pas dupliquer les informations (ou les médias). Ainsi, en réduisant la quantité, on peut réduire l'impact.  
Par exemple : le DAM : une seule image de meilleure qualité que l’on peut implémenter partout en jouant sur sa qualité/ ses dimensions, plutôt que d’avoir une multitude de versions de la même image stockées (grâce à un outil de DMO).

{% info %}

Pour info, si vous voulez tester votre site internet sur son utilisation des médias et savoir s'il serait possible de l’améliorer d’un point de vue de la sobriété numérique, le site de Scalflex propose un outil de diagnostic : [Run our test to find out your web performance](https://www.scaleflex.com/website-performance-and-carbon-calculator?utm_source=livestorm&utm_medium=webinar&utm_campaign=2024Q1-archimag-dam-pim-sustainability-belco#cloudimage)

J’ai fait le test pour le site de Centrale Méditerranée et le résultat est plutôt bon :  
En moyenne, les sites peuvent obtenir une réduction de 400% de leurs émissions carbone grâce à leurs solutions et celui de Centrale, seulement 11%, ce qui veut dire qu’il est déjà plutôt bien pensé.

{% endinfo %}

### RETEX

Ce MON a été pour moi l’occasion de prendre le temps de me documenter sur chacun de ces outils faisant partie du système d’information lié à la donnée produit, qui sont au cœur de mon travail en alternance. Je suis donc satisfaite d’avoir pu prendre le temps de le faire et de ce que j’ai pu apprendre.

Un problème que je pourrais soulever sur ces sujets, qui sont très liés à des solutions et donc à des produits vendus par des marques, c’est que l’information que l’on trouve en ligne est très destinée à des consommateurs et donc ne met peut-être pas assez en relief les réelles limites des différentes solutions, mais s’axe beaucoup plus sur les possibilités et avantages de celles-ci. C’est donc intéressant d’un point de vue professionnel, mais il manque un point de vue critique.

Ma rédaction manquera alors peut-être de nuances, mais ce MON pourra servir à ceux qui auraient besoin de savoir les utilités spécifiques de chacun de ces outils, et j’espère que le tableau récapitulatif permettra à ceux en ayant besoin d’avoir une vision assez synthétique de ce panorama des éléments qui composent un système d’information orienté autour de la donnée produit.

### Horodatage

| Date | Heures passées | Indications |
| -------- | --------- | --------|
| Samedi 16/02 | 1h | Recherche documentation |
| Dimanche 17/02 | 2h | Documentation PIM, PLM |
| Lundi 18/02 | 3h | Documentation DAM, MDM, GED, ETL, Datamart |
| Mercredi 19/02 | 0h30 | Webinaire PIM, PLM, MDM, … |
| Jeudi 20/02 | 0h30 | Vidéo Sobriété numérique |
| Vendredi  20/02 | 2h | Comparaison des différents SI |
| Mercredi  26/02 | 2h | Enjeux |

### Bibliographie

{% lien %}

- [Product information management](https://en.wikipedia.org/wiki/Product_information_management)
- [PIM NextPage](https://www.nextpage.fr/qu-est-ce-qu-un-pim/)
- [PLM : Gestion du cycle de vie de produit](https://blog-gestion-de-projet.com/gestion-de-projet/plm/)
- [Gestion du cycle de vie (produit)](https://fr.wikipedia.org/wiki/Gestion_du_cycle_de_vie_(produit))
- [Qu'est-ce que le Digital Asset Management ? Définition & Ressources](https://www.bynder.com/fr/blog/quest-ce-que-le-digital-asset-management-dam/)
- [Données Produits : Comparaison PIM vs. MDM vs. DAM vs. PLM](https://www.akeneo.com/fr/blog/product-data-solutions-breakdown/?utm_source=chatgpt.com)
- [GED, PIM, BAM, DAM : quelles sont les différences entre ces solutions ?](https://www.cotranet.com/ged-pim-bam-dam-quelles-sont-les-differences-entre-ces-solutions/?utm_source=chatgpt.com)
- [Webinaire : PIM, PLM, MDM, GED, DAM, pique et pique et colegram !](https://youtu.be/XCRFVG0TC-k?feature=shared)
- [Webinar : DAM-PIM : L’expérience produit réussie dans un contexte de sobriété avec Scaleflex et Akeneo](https://youtu.be/NcUHi7F0IBU?feature=shared)

{% endlien %}
