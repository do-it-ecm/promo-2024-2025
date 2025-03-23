---
layout: layout/mon.njk

title: "Architecture d'entreprise et modélisation"
authors:
  - Alix Duréault

date: 1971-03-01
temps: 3
tags:

description: "Comment modéliser la structure et les process d'une entreprise ?"
---

Le but de ce MON est à la fois d'approfondir les notions que nous avons pu aborder dans le cours de Conception des SI sur la modélisation des process d'une entreprise notamment avec le logiciel Byzagi mais aussi d'explorer la notion d'architecture d'entreprise que j'ai pu entendre lors de mes entretiens pour des stages en conseils dans le digitale et la transformation digitale.

{% sommaire %}

${toc}

{% endsommaire %}

## Contenu

### Qu’est ce que l’architecture d’entreprise ?

{% details "**Sources**" %}

- Architecture d'entreprise - Page Wikipédia

- [Jeanne Ross of MIT CISR on Enterprise Architecture](https://www.youtube.com/watch?v=feI6_-v10Dk)

{% enddetails %}

D’après la page Wikipédia dédiée à ce sujet, l’architecture d’entreprise a pour but “d'aligner la stratégie du système d'information sur la stratégie des organisations.” Pour cela, elle s’appuie sur différents frameworks ou cadres d’architecture.

Elle vise à représenter l’entreprise sous forme de composants en se concentrant sur la structure, les interactions et la cohérence entre ceux-ci. Elle cherche donc à représenter les processus, les informations, les applications et l'infrastructure. Elle a pour ambition de faire participer les acteurs métiers à la mise en œuvre du système d'information.

L’architecture d’entreprise est aussi une logique pour les compétences en procédés commerciaux, data et IT qui permet de réfléchir à l’intégration et la standardisation des exigences d’un modèle d’opération d’une entreprise. Mais aussi elle permet d’obtenir un design d’une ou plusieurs plateformes digitales, elles contiennent des compétences essentielles permettant l’agilité. La plateforme digitale dont il est question est un ensemble cohérent de process commerciaux standardisés avec une infrastructure, des applications, des données qui assure sa qualité et la predictabilité des transactions principales.

Les différents frameworks que l’on peut citer sont :

- Le cadre Zachman : a posé les bases, pionnier, structure en matrice permettant de décrire l’entreprise à travers différentes perspectives et niveaux d'abstraction.
- The Open Group Architecture Framework : le plus populaire, approche détaillée (outils, techniques et méthodologie claire), comprend quatre domaines (l'architecture métier, l'architecture des données, l'architecture applicative et l'architecture technique)
- ArchiMate : outil de cartographie, langage de modélisation
- FEAF : par le gouvernement des Etats Unis pour les agences fédérales
- Gartner Enterprise Architecture Framework : approche basée sur les résultats et la valeur pour l’entreprise
- DoDAF : framework de l’armée des Etats Unis
- SABSA : framework pour la cybersécurité
- DYNAMAP : framework simplifié

L’architecture peut contribuer à une meilleure agilité de l’entreprise et de son système d’information. Elle peut néanmoins être difficile à mettre en place à cause de la résistance au changement, la complexité des cadres, la nécessité de coopération.

### Exploration de quelques frameworks d’architecture d’entreprise

#### The Open Group Architecture Framework (TOGAF)

{% details "**Sources**" %}

- [The Open Group Architecture Framework](https://en.wikipedia.org/wiki/The_Open_Group_Architecture_Framework)

- [TOGAF sur opengroup.org](https://www.opengroup.org/togaf)

- [TOGAF 10 simplified de Go Cloud Architects](https://www.youtube.com/watch?v=FG7e2fYCz80)

{% enddetails %}

C’est le framework le plus utilisé en 2020. Il propose une démarche pour le design, la planification, l’implémentation et la gouvernance du système d’information et de son architecture. La structure de la méthode est représenté par le schéma suivant. La méthode est itérative et cyclique et surtout fais toujours le lien avec les demandes et enjeux.

![Schéma de la méthode TOGAF](https://www.opengroup.org/sites/default/files/adm.png)

L’approche est modélisé sur plusieurs niveaux : Business, Application, Data, and Technology. Elle repose sur de la modularisation, de la standardisation, des technologies et produits existants.

Ce framework permet de spécifier 4 sous-domaines de l’architecture d’entreprise :

- “Business Architecture” : la stratégie business, la gouvernance, l’organisation et les process clés de l’organisation.
- “Data architecture” : la structure des données physiques et logiques et les ressources de management de données
- “Applications architecture” : plan des applications individuelles et de leurs interactions
- “Technical architecture” : description de l’infrastructure réseaux, hardware et software.

Ce framework est critiqué pour des manquements à la méthode, une difficulté d’implémentation en tant que méthodologie pas à pas, des prescriptions vagues.

#### The Sherwood Applied Business Security Architecture (SABSA)

{% details "**Sources**" %}

- [Sherwood Applied Business Security Architecture](https://en.wikipedia.org/wiki/Sherwood_Applied_Business_Security_Architecture)

- [Understanding SABSA - medium.com](https://medium.com/@tahirbalarabe2/understanding-sabsa-the-sherwood-applied-business-security-architecture-d2b4e78679e5)

- [The SABSA Institute](https://sabsa.org/sabsa-executive-summary/)

{% enddetails %}


Ce framework permet de développer une architecture de sécurité des informations d'entreprise axée sur le risque et une gestion des services. Sa particularité est que tout doit être dérivé d'une analyse des besoins métier en matière de sécurité. Le modèle est structuré en couches, la couche supérieure étant celle de la définition des besoins métier. À chaque couche inférieure, un nouveau niveau d'abstraction et de détail est développé.

La méthode repose sur certains principes fondamentaux : orientée métier, gestion des risques, approche du cycle de vie, adaptabilité, évolutivité et modularité. L’approche cycle de vie signifie que la sécurité est maintenue tout au long de la vie du système définie en 6 phases (stratégie et planification, conception, mise en oeuvre, opérations, surveillance et examen, maintenance et amélioration).

Cette méthode a développé une matrice qui a ensuite été complété par une matrice de gestion des services. Cette matrice détailles les différentes couches d’architecture : architecture de sécurité contextuelle, conceptuelle, logique, physique, des composants et opérationnelle.

Cette méthode présente plusieurs avantages, elle s’aligne avec les objectifs commerciaux, elle a une approche axée sur les risques, elle offre une couverture complète, elle est flexible et évolutive et elle aborde une démarche d’amélioration continue.

#### DYNAMAP

{% details "**Sources**" %}

- [DYNAMAP](https://www.dynamap.fr/)

- [DYNAMAP - Le framework](https://www.dynamap.fr/le-framework/)

{% enddetails %}


DYNAMAP est un framework qui cherche à offrir non pas un remplacement des autres frameworks mais plutôt une solution plus simple et incrémentale, moins complexe et plus rapide.

La démarche est tournée autour de la cartographie du SI. Et se déroule en plusieurs phases présentées dans le schéma suivant :

L’avantage de se framework est qu’il est incrémental, chaque étapes et détail peut être adapté à l’organisation dont il est question. Il repose aussi sur des techniques de visualisation et de cartographie poussée et dynamiques.

### Mise en lien avec mon TFE et le management des SI

Ce sujet m’intéresse notamment car il se rapproche beaucoup à la conception des SI, là où j’ai pu le découvrir mais aussi à mon TFE qui va tourner autour de la transformation digitale des entreprises. Ainsi, dans cette partie, je me suis concentrée sur explorer le rapport entre le sujet, la transformation digitale et les SI.

#### Transformation digitale et Architecture d’entreprise

{% details "**Sources**" %}

- [Architecture d'entreprise au service de la transformation digitale](https://www.cesames.net/architecture-dentreprise/)

- [Mémoire de Jean-Marc Auvray - Définition et mise en œuvre de la transformation digitale au sein d’une entreprise de type PMI/PME, ETI : proposition d’une démarche d’analyse et de transformation](https://dumas.ccsd.cnrs.fr/dumas-01729148v1/file/2017.TH.Auvray.Jean-Marc.pdf)

{% enddetails %}

En utilisant l’architecture d’entreprise au service des transformations digitales, cela permet de prendre cette transformation comme une transformation globale d’entreprise et de faciliter l’alignement des technologies, des objectifs stratégiques, des activités, des méthodes de travail et des besoins métiers. En décrivant l’entreprise comme un système avec des métiers et une partie technique interdépendants, cela permet des analyses plus complètes et des décisions plus éclairées.

L’incorporation d’une stratégie d’architecture d’entreprise permettrait de garder en tête non seulement les objectifs mais aussi les personnes qui sont concernées par les modifications. L’architecture d’entreprise permet d’aligner les stratégies entreprise, SI et commercial.

Dans le mémoire rédigé par Jean Marc Auvray, l’auteur souligne l’importance d’intégrer des structures organisationnelles plus “agiles et plus réactives” dans des entreprises assez “classiques” afin de pouvoir assurer ces transformation digitale et pouvoir suivre les évolutions technologiques rapide. L’architecture d’entreprise permet de gérer la complexité en comprenant, analysant le fonctionnement de l’entreprise.

De plus, la stratégie lié au SI et les stratégies liées aux transformations digitales ont besoin d’un alignement métier. Connaître les processus métiers permet de créer de la valeur, de la compétitivité et d’assurer la performance.

### Modélisation

{% details "**Sources**" %}

- [Mémoire de Jean-Marc Auvray - Définition et mise en œuvre de la transformation digitale au sein d’une entreprise de type PMI/PME, ETI : proposition d’une démarche d’analyse et de transformation](https://dumas.ccsd.cnrs.fr/dumas-01729148v1/file/2017.TH.Auvray.Jean-Marc.pdf)

- [Comparaison de trois techniques de modélisation de processus: ADONIS, OSSAD et UML - Olivier Glassey et Jean-Loup Chappelet](https://serval.unil.ch/resource/serval:BIB_25583.P001/REF.pdf)

- [BPMN 2.0 - Blueway](https://www.blueway.fr/blog/norme-bpmn)

- [BPMN - Wikipédia](https://fr.wikipedia.org/wiki/Business_process_model_and_notation)

{% enddetails %}

Il existe plusieurs méthodes de modélisation et langages de modélisation. Aucun n’est particulièrement complet et ne permet de modéliser tous les aspects d’un système.

- UML : référence, le plus largement utilisé
- ADONIS : logiciel de modélisation de processus opérationnel qui intègre sa propre technique de modélisation
- BPMN : pour la modélisation des processus métiers,, permet la complexité, notation standardisé (norme ISO)
- OSSAD : pour l’analyse de l’activité, facilité d’apprentissage, réingénérie des systèmes, modélisation graphique d’organisation
- IDEF0 : efficace pour l’analyse, ne permet pas la réingénierie de systèmes.
- Merise : préconise un découpage fonctionnel, destinée aux systèmes structurés et stables
- DMN : modélisation des décisions
- CMMN : gestion des cas

Les différents modèles couvrent des champs d’application qui ne sont pas toujours similaires. mais ont globalement tous pour objectif de représenter la réalité avec des points de vue et des niveaux différents. Voici quelques particularités qui ont pu être mises en avant dans la recherche de Olivier Glassey et Jean-Loup Chappelet :

→ Adonis permet de différencier rôles et acteurs.

→ UML permet de modéliser n’importe quel type de ressources.

→ UML est une méthode de conception de systèmes informatiques et elle ne s’intéresse de ce fait pas à la hiérarchie ou à la structure d’une organisation.

→ Le modèle de procédures d’OSSAD est lié au modèle abstrait car chaque procédure représente une activité du modèle abstrait.

→ BPMN vise l'analyse et la conception des processus métiers qui font intervenir et interagir des systèmes.

Explorons certaines de ces méthodes.

#### Office Support Systems Analysis and design (OSSAD)

{% details "**Sources**" %}

- [OSSAD - page Wikipédia](https://fr.wikipedia.org/wiki/Office_support_systems_analysis_and_design)

- [L’importance de la méthode OSSAD pour documenter les processus d’affaire - ETS](https://publicationslist.org/data/a.april/ref-405/IIBAv2.pdf)

- [Comparaison de trois techniques de modélisation de processus: ADONIS, OSSAD et UML - Olivier Glassey et Jean-Loup Chappelet](https://serval.unil.ch/resource/serval:BIB_25583.P001/REF.pdf)

{% enddetails %}

C’est une méthode ouverte, non propriétaire et standard d'analyse d'organisation par les processus des systèmes de management et des systèmes d'information associés. Elle est utilisée en tant qu’outil de modélisation et de description des processus organisationnels.

Cette méthode respecte les normes ISO en systèmes de management (ISO 9001, 14001, 27001, …). Ces normes recommandent une représentation des organisations selon une approche processus, une approche par les risques et pilotée par des indicateurs permettant de corriger les non-conformités et défauts.

Elle propose un langage commun facilement assimilable par tous les acteurs du changement. Utiliser une visualisation graphique permet une visualisation cohérente et synthétique de l'organisation, une compréhension de fonctionnements complexes et une participation facilitée à la rédaction, lecture, validation, application, appropriation par tous et audit des documents.

Pour éviter les limites de la description linéaire (peu d’abstraction, pas de rôle, lourdeur des notations, ….), OSSAD utilise trois strates : processus, procédures et instructions de travail. La méthode permet de maîtriser la gestion des données d'un système grâce à une « grammaire graphique ».

Ainsi, la méthode s’appuie sur 3 modèles qui représentent ces trois strates :

- Abstrait : modélisation graphique des processus, décrit les objectifs de l’organisation, représente les fonctions de l’organisation et les paquets d’information qu’elles échangent, permet de visualiser les flux, identifier les interactions à considérer lorsque des modifications sont envisagées dans une partie ou l'autre du modèle.

- Descriptif : modélisation graphique des procédures, décrit les moyens humains et les ressources technologiques de l’organisation. Il se compose de trois types de formalismes graphiques (matrice activités/rôles, graphe de circulation des ressources d’informations, graphe d’opérations).

- Prescriptif : modélisation graphique des instructions de travail, facultatif, établir le pont avec des méthodes et outils de développement d’applications.

Quelques outils permettent d’utiliser cette méthode comme OSS@D Process Design.

#### Adonis

{% details "**Sources**" %}

- [Comparaison de trois techniques de modélisation de processus: ADONIS, OSSAD et UML - Olivier Glassey et Jean-Loup Chappelet](https://serval.unil.ch/resource/serval:BIB_25583.P001/REF.pdf)

{% enddetails %}

Adonis est un logiciel de modélisation de processus opérationnel qui intègre sa propre technique de modélisation et son langage de description propriétaires.

La méthode est propriétaire et totalement intégrée avec l’outil du même nom. Il contient un module d’acquisition de données qui permet par exemple d’importer des statistiques en format Excel ainsi qu’un module de modélisation graphique. L’outil Adonis permet par ailleurs d’effectuer des analyses poussées grâce à son langage d’interrogation intégré et de procéder à des simulations basées sur des algorithmes de calcul de chemin, de temps ou de coûts.

La modélisation standard d’Adonis repose sur trois types de modèles :

- Carte des processus : donne une idée des différents processus ou sous-processus

- Modèle d’environnement de travail : représenter la structure d’une organisation en termes d’unité, de responsables et de rôles, prend en compte les ressources disponibles

- Modèle de processus opérationnel : représenter le chemin suivi par un processus depuis son début jusqu’à sa fin, intègre la notion d’acteurs et de ressources

#### Unified Modeling Language (UML)

{% details "**Sources**" %}

- [Comparaison de trois techniques de modélisation de processus: ADONIS, OSSAD et UML - Olivier Glassey et Jean-Loup Chappelet](https://serval.unil.ch/resource/serval:BIB_25583.P001/REF.pdf)

{% enddetails %}

UML est un langage de notation graphique standardisé qui peut être utilisé dans différents domaines de modélisation et notamment pour décrire des processus de gestion. Il existe des dizaines de logiciels qui supportent UML, comme Rational Rose ou UMLStudio.

C’est un langage orienté objet. Il couvre les différentes phases d’un développement objet (analyse, conception et implémentation) avec 9 types de diagrammes :

- Diagramme de cas d’utilisation : représente les comportements d’un système avec son environnement et les acteurs qui le constituent du point de vue de l’utilisateur

- Diagramme de classes (structure statique d’un système sous la forme de classes et de relations)

- Diagramme d’objets (représente les objets et leurs relations)

- Diagramme de séquence : représente les objets et leurs interactions dans la temporalité

- Diagramme de collaboration : représente les objets, leurs liens et leurs interactions sous un angle structurel

- Diagramme de transition d’états (comportement dynamique d’un objet en termes d’états, d’activités, de transitions et d’événements)

- Diagramme d’activités : flux de contrôle et d’information qui circulent entre activités au sein d’un système. Ils permettent de représenter le séquencement exact des activités et de définir des conditions d’exécution

- Diagramme de composants (implémentation physique d’un système)

- Diagramme de déploiement (décrit la configuration des éléments de traitement à l’exécution et les composants qui leur sont rattachés)

#### Business Process Model and Notation (BPMN 2.0)

{% details "**Sources**" %}

- [Norme BPMN 2.0 - Axelor](https://axelor.com/fr/la-norme-bpmn/)

- [Norme ISO 19410](https://www.iso.org/fr/standard/62652.html)

- [BPMN Specification - BPMN](https://www.bpmn.org/)

- [BPMN 2.0 - Blueway](https://www.blueway.fr/blog/norme-bpmn)

- [BPMN - Wikipédia][https://fr.wikipedia.org/wiki/Business_process_model_and_notation)

{% enddetails %}

Les lettres BPM renvoient à la gestion des processus métier (analyse, amélioration, modélisation et automatisation des process de l’organisation et leur suivi dans le temps). La lettre N renvoie quant à elle à la notation. La norme  BPMN est une méthode de modélisation des processus métier à travers une représentation graphique.

La norme BPMN est régie par la norme internationale ISO/CEI 19510.

La modélisation BPMN peut être utilisée dans tous les secteurs d’activité et pour tous les types de processus. Elle se concentre néanmoins sur l’analyse et la conception des processus métier sous forme de diagrammes.

La norme BPMN 2.0 est constituée d’un ensemble d’éléments graphiques avec 4 élèments de base :

- Les activités (description de l’action à mener à une instance du processus comme une tâche, une transaction, un appel, un sous-processus)
- Les branchements et connecteurs (connecteurs, séparer et associer les flux, relier les objets)
- Les évènements (évènements au sein du processus, début, fin, intermédiaire, …)
- Les passerelles (orienter les flux vers les étapes suivantes)