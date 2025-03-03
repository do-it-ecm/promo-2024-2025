---
layout: layout/mon.njk

title: "MON 3.2 - RGPD spécifique aux données médicales"
authors:
  - Emma Gonin

date: 2024-12-16
temps: 3
tags:

résumé: "Un MON traitant de la RGPD, axée sur les données médicales."
---

{% prerequis %}
Aucun prérequis !
{% endprerequis %}
{% lien %}

[La CNIL](https://www.cnil.fr/fr/le-rgpd-applique-au-secteur-de-la-sante)
[L'utilisation des données de santé](https://www.legalplace.fr/guides/rgpd-donnees-sante/)
{% endlien %}

Toutes mes expériences professionnelles ont été dans le domaine du médical, avec du traitement de données d'imagerie médicales. Je souhaite retranscrire dans ce MON la réglementation liée à ces données médicales et comment l'appliquer en tant qu'ingénieur, dans sa pipeline de données.

## Guide de l'ingénieur traitant de données médicales

### Délimiter le périmètre
Quelle est la finalité du traitement de ces données de santé ?

### D'où viennent les données de santé ?

#### Si les données sont collectées par nous-mêmes

* Comment collecter des données de santé ?
  * Recueillir le consentement des personnes concernées par un traitement de données, à la fois dans le cadre de la collecte mais aussi en cas de modification susbtantielle ou d'évènement particulier;

* Comment conserver des données de santé ?
  * La durée de conservation qui dépend de si c'est pour faire de la recherche ou non
   * 10 ans 
  * Où les stocker ? 
    * Entrepôts de données de santé
    * Recherche
    * Hébergeur de données de santé : ([Liste des hébergeurs certifiés "HDS"](https://esante.gouv.fr/offres-services/hds/liste-des-herbergeurs-certifies))

#### Si les données d'un tiers sont utilisées

Sources de données de santé :
* [data.gouv.fr](https://www.data.gouv.fr/fr/pages/donnees_sante/) recense dans la partie dédiée à la santé les sources publiques de données;
  Par exemple : 
  * La caisse nationale de l'assurance maladie gère plusieurs bdd;
  * L'agence régionale de santé...

### Réglementation relative aux données de santé : cadre juridique

Les données de santé sont des données sensibles dont le traitement est sujet à différentes réglementations.

* Loi Informatique et Libertés ([art. 8 et chapitre IX](https://www.cnil.fr/fr/la-loi-informatique-et-libertes))
* Dispositions sur le secret ([art. L. 1110-4 du Code de la Santé Publique](https://www.legifrance.gouv.fr/codes/id/LEGIARTI000036515027/2018-01-19/)) 
* Dispositions relatives aux référentiels de sécurité et d'interopérabilité des données de santé ([art. L. 1110-4-1 du CSP](https://www.legifrance.gouv.fr/codes/id/LEGIARTI000038886960/2019-07-27/)) 
* Dispositions sur l'hébergement des données de santé ([art. L. 1111-8 et R. 1111-8-8 et s. du CSP](https://www.legifrance.gouv.fr/codes/id/LEGIARTI000033862549/2018-04-01/)) 
* Dispositions sur la mise à disposition des données de santé ([art. L. 1460-1 et s. du CSP](https://www.legifrance.gouv.fr/codes/id/LEGIARTI000038886892/2019-06-02/)) 
* Interdiction de procéder à une cession ou à une exploitation commerciale des données de santé ([art. L. 1111-8 du CSP](https://www.legifrance.gouv.fr/codes/id/LEGIARTI000021941353/2012-07-28/), [art. L 4113-7 du CSP](https://www.legifrance.gouv.fr/codes/id/LEGIARTI000021941353/2012-07-28/))
 
La [vidéo](https://www.youtube.com/watch?v=aGisMwPoBG8&t=19s&ab_channel=AgenceduNum%C3%A9riqueenSant%C3%A9) de l'ANS sur les réglementations pour les start-up en e-santé cite également les textes spécifiques au secteurs de la santé :
* Règlements européens portant sur les dispositifs médicaux;
* Espace européen des données de santé;
* Politique de la Gestion de la Sécurité des Systèmes d'Information de Santé (PGSSI-S);

### Boîte à outils
J'ai suivi de courtes formations sur le site d'[ANS-Formation](https://www.coorpacademy.com/ans-formation/) proposé par l'Agence du Numérique en Santé. Ces formations sont accessibles au grand public, allant des étudiants aux médecins en passant par les curieux.
La question qui régit ce MON étant comment appliquer le RGPD en santé, j'ai regardé la leçon dédiée à ce sujet. 
En voici un résumé :

* Premier outil à mettre en place et obligatoire : le **registre des activités de traitement**. Cette documentation est une vue d'ensemble de la gestion des données personnelles. 
Il contient : 
  * Les parties prenantes (des sous-traitants aux co-responsables);
  * La finalité du traitement;
  * Les catégories de données traitées;
  * Les catégories de destinataires de données traitées;
  * La durée de conservation des données;
  * Les transferts de données hors UE;
  * Les modalités d'information et d'exercices des droits;
  * La manière dont les données sont sécurisées.

Chaque représentant de chaque sous-traitant tient un registre de toutes les catégories d'activités de traitement du sous-traitant.

Ces documents sont consultables par la CNIL mais aussi par un juge dans un cadre de procédure pénale.

* Second outil fortement conseillé dans le cadre de traitement de données de santé : une **Analyse d'Impact relative à la Protection des Données** (AIPD). 
Cette analyse est obligatoire lorsque le traitement des données est susceptible d'engendrer un risque élevé pour les droits des libertés des personnes concernées, par exemple dans le cadre de traitement des données à grande échelle.
Elle contient : 
  * Une description détaillée, à la fois technique et organisationnelle, du traitement;
  * La nécessité et proportionnalité concernant les principes et droits fondamentaux (finalité, durée de conservation, droits des personnes...);
  * Une étude des risques sur la sécurité des données qui détermine les mesures techniques à prendre.

* La nomination d'un **Délégué à la Protection des Données** obligatoire dans trois cas :
  * Autorités ou organismes publics (hopitaux, autorités sanitaires...);
  * Organismes dont l'activité de base est le suivi régulier des personnes à grande échelle (objets connectés surveillant les données de santé);
  * Organismes dont l'activité de base est le traitement à grande échelle des données sensibles (laboratoire de données médicale)

Cependant, en e-santé, les autorités encouragent la nomination d'un DPO. Le DPO peut être interne ou externe à l'organisation mais ne peut pas prendre des décisions sur les moyens de traitements, sinon il y a des conflits d'intérêts. Par exemple, un médecin-chef, un PDG d'entreprise ou un responsable IT ne peut pas être DPO. 
On peut avoir recours à des DPO venant de cabinet de conseil ou de cabinet d'avocat.

### Risques
* Fuites de données à cause de règles de sécurité insuffisantes.

  Par exemple, le mauvais paramètrage d'un service de cloud Amazon a causé la fuite de 47,5 Go de données provenant d'un service de surveillance de patients à domicile. En France il n'est pas possible d'héberger des données de santé sur Amazon, comme vu plus haut, nous avons l'obligation d'utiliser des hébergeurs de données de santé. Ce n'est pas le cas aux Etats-Unis, où cette erreur s'est passée. [Lien de l'article](https://dsih.fr/articles/2672/les-dossiers-medicaux-de-150-000-patients-americains-en-acces-libre-sur-le-cloud-damazon)

* Piratage, destruction et rançonnage de données.

  En 2017, le virus Wannacry a touché des dizaines d'hôpitaux, notamment au Royaume-Uni. « L'attaque a sérieusement désorganisé des dizaines d'hôpitaux, contraints d'annuler certains actes médicaux et de renvoyer des ambulances vers d'autres établissements [»](https://www.lesechos.fr/2017/05/cyberattaques-les-hopitaux-britanniques-principales-cibles-atteintes-168007).


## Ressources
* [G_nius](https://gnius.esante.gouv.fr/fr) est le Guichet national de l'innovation et des usages en e-santé, action de l'Agence du numérique en santé, soutient et accompagne les entrepreneurs en e-santé.
* Le site https://industriels.esante.gouv.fr/ est la partie du site de l'ANS dédiée aux industriels. 
* La [Doctrine du numérique en Santé](https://industriels.esante.gouv.fr/sites/default/files/media/document/Doctrine_2023.pdf) est le document référence pour les acteurs de la e-santé. 
* [Fiche introduction aux bonnes pratiques de traitement de données de santé](https://industriels.esante.gouv.fr/sites/default/files/media/document/innovation/20221025_ANS-DEII_Innovation_PSC_Fiche-Synthetique_Donnees-de-sante_V1.2.pdf) proposée par l'ANS.
* https://www.cnil.fr/fr/quelles-formalites-pour-les-traitements-de-donnees-de-sante
* https://www.cnil.fr/fr/traitements-de-donnees-de-sante-comment-faire-la-distinction-entre-un-entrepot-et-une-recherche-et
* https://www.cnil.fr/fr/traitement-de-donnees-de-sante-comment-informer-les-personnes-concernees
* [Feuille de route du gouvernement concernant le numérique et la santé](https://industriels.esante.gouv.fr/sites/default/files/media/document/dns-feuille-de-route-2023-2027.pdf)
