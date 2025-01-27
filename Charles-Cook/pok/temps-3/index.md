---
layout: layout/pok.njk

title: "Introduction au NLP"
authors:
  - Charles Cook

date: 1971-03-01

temps: 3
tags:

résumé: L'objectif de ce POK est de découvrir le NLP (Natural Language Processing).
---

{% prerequis %}

Liste des prérequis du POK ET/OU MON

{% endprerequis %}
{% lien %}

Les lien utiles pour la compréhension de celui-ci.

{% endlien %}

## Cadrage

### Objectifs principaux
1. Comprendre les mécanismes de base du NLP
2. Appliquer une clusterisation thématique et une analyse sentimentale à un exemple.
3. Introduction au système de mise en place d'un chatbot

### Monitoring du projet
#### Back-log et Horodateur
{% details "Sprint 1" %}
- [x] Trouver des ressources pour comprendre ce qu'est le NLP
- [x] Création d'une base de données exploitable pour l'exemple
- [x] Mise en place une analyse sentimentale
- [x] Etude de l'analyse sentimentale
- [ ] Mise en place d'une clusterisation thématique
- [ ] Etude de l'analyse thématique

| Date | Heures passées | Indications |
| -------- | -------- | -------- |
| 19/01/2025 | 0.5h | Cadrage projet |
| 19/01/2025 | 2.5h | Compréhension des différents types de NLP et des processus sous-jacents |
| 20/01/2025 | 0.5h | Création de la première base de donnée |
| 22/01/2025 | 1.5h | Analyse sentimentale et étude des résultats |
| 24/01/2025 | 1.0h | Nouvelles base de données et analyse sentimentale |
| 25/01/2025 | 2.0h | Recherches sur la clusterisation |
| 26/01/2025 | 2.0h | Tentative de codage d'une focntion de clusterisation |
| 26/01/2025 | 1.0h | Rédaction du sprint 1 |

{% attention %}
La mise en place d'un code permettant d'automatiser une clusterisation thématique n'a pas été une réussite en sprint 1.
{% endattention %}
{% enddetails %}

{% details "Sprint 2" %}
- [ ] Fin éventuelle de l'analyse textuelle du premier sprint
- [ ] Etude du NLP dans le cadre d'une analyse vocale
- [ ] Réalisation d'un exemple permettant de comprendre le fonctionnement
- [ ] Etude de mise en place en entreprise

| Date | Heures passées | Indications |
| -----|----------------|-------------|
| 01/01/2025 | Xh | Blablabla |

{% enddetails %}

#### Analyse post-morterm

{% details "Sprint 1" %}
**GESTION GENERALE DU TEMPS :** Bonne estimation générale dans le nombre de tâches pour le temps 1. Cependant, des difficultés et points bloquants n'ont pas été anticipé, ne permettant pas de terminer la totalité des tâches qui avaient été fixées. Celles-ci serton reprises en début de sprint 2.

**DIMENSIONNEMENT DES TACHES :** Les tâches auraient pû être plus précises. Cela aurait permis de moins perdre de temps dans la mise au travail pour chacune de celle-ci. L'ordre de celles-ci a cependant été suivi et réaliste. 
{% enddetails %}
{% details "Sprint 2" %}
Blabla
{% enddetails %}
{% details "POK GLOBAL" %}
Blabla
{% enddetails %}

## Analyse Textuelle
### Contexte
Nous nous plaçons dans le cas d'une entrepise qui possède énormément de données textuelles (réponses à des questions ouvertes d'un sondage, commentaires laissés sur google, réseaux sociaux). L'objectif est donc de tirer des apprentissages de cette quantité de données et de mettre en place des plans d'action. 

### Démarche générale pour l'entreprise
1. Analyse sentimentale afin de déterminer si l'échantillon textuel est positif ou négatif.
2. Clusterisation afin de classer les échantillons textuels par thématique.
3. Plans d'action par thématique en fonction du résultat de l'analyse sentimentale.

### Analyse sentimentale
{% details "Approche méthodologique" %}
- Création d'une base de données comprenant les notes et commentaires associés laissés par les spectateurs sur le film "The Substance" par Coralie Fargeat.
- Analyse sentimentale en attribuant un indice de positivité sur chacun des commentaires.
- Etude de la corrélation entre les notes attribuées par les spectateurs et l'indice de positivité. 
{% enddetails %}
{% details "Nettoyage et standardisation des données" %}
Cette préparation préalable se fait avec les étapes suivantes : 
- **Etape 1 : Suppression des données manquantes**<br>
*Fonction employée :* `dropna`
- **Etape 2 : Nettoyage du texte**<br>
**Conversion des caractères en minuscule** <br>
*Fonction employée :* `str.lower()`<br>
**Suppression des caractères spéciaux** <br>
*Fonction employée :* `apply(lambda x: re.sub(r"[^a-zA-Z0-9\s]", "", x))`<br>
**Suppression des espaces multiples** <br>
*Fonction employée :* `apply(lambda x: re.sub(r"\s+", " ", x).strip())`<br>
- **Etape 3 : Tokenisation**<br>
*Explication :* Transforme une chaîne de caractère en liste de mots.<br>
*Fonction employée :* `apply(word_tokenize)`<br>
- **Etape 4 : Lemmatisation**<br>
*Explication :* Réduit les mots à leur forme canonique (infinitif des verbes par exemple).<br>
*Fonction employée :* `lemmatizer = WordNetLemmatizer()`<br>
{% enddetails %}
{% details "Attribution d'un indice de polarité" %}
- *Méthode :* A partir d'un dictionnaire préconstruit, une polarité est attribué à chaque mot (*merveilleux* aura une polarité positive tandis que *mauvais* ara une polarité négative).
- *Bibliothèque utilisée :* TextBlob
- *Avantages :* Analyse sentimetale intégrée, peu de code, bon pour des projets simples, compatible en français.
{% enddetails %}
{% details "Résultats" %}
On remarque que dans le cadre des commentaires sur le film "The Substance", la corrélation entre la note et la polarité n'est pas évidente. Ceci peut s'expliquer par le fait qu'il s'agit d'un film de body horror. Des commentaires possèdent donc des mots comme "gore", "horrible", "dégoûtant" mais ont de très bonnes notes.<br>

**Réitérons l'expérience avec une base de données comprenant les commentaires laissés sur un bar avec leurs notes associées.**
On remarque alors que la corrélation est beaucoup plus éviente. Ce code permet donc de déterminer automatiquement si un commentaire est plutôt positif ou négatif.
{% enddetails %}

### Clusterisation
{% details "Approche méthodologique" %}
- Nettoyer les données en faisant une pré-analyse (comme pour l'analyse sentimentale).
- Représenter chaque mot sous forme de vecteur, appelé *Word Embedding*. Il s'agit de représenter une chaîne de caracatère en vecteur numérique de taille fixe. Les mots ayant un sens proche ont une représentation proche dans l'espace vectoriel.
- Classification des vecteurs par la méthode des k-means.
{% enddetails %}
{% details "Algorithme des k-means" %}
- Initialisation avec k le nombre de cluster souhaité. 
- Choix de k individus au hasard (représentant les k classes à ce stade).
- Association de chacun des individus restant à la classe la plus proche.
- Carcatérisation de chacune des classes par la moyennes de points qu'elle contient.
- Evaluation de la distance physique de chacun des individus à chacune des k moyennes. Les individus peuvent alors changer de classe si une autre est plus proche.
- Ré-itération de l'étape précédente jusqu'à ce qu'il n'y ait plus de changement de classe parmis les individus. 
- Obtention des k clusters.
{% enddetails %}
{% details "Code" %}
- *Bibliothèque utilisée :* `Pycaret`
- *Avantage :* réalise le pré-traitement des données, encode les données (attribue un vecteur à chaque commentaire textuel), clustering intégré.
{% enddetails %}
{% details "Résultats" %}
La base que j'ai utilisée est la base de 50 commentaires sur le bar avec les notes associées. Pour faire tourner le modèle j'ai choisi un k de 2 afin d'obtenir 2 clusters. Le problème est que l'lagorithme semble bien s'éxécuter mais lorsque j'essaie d'afficher les données dans un graphique (un graphique en barre par exemple pour obtenir la population de chacun des clusters), mon ordinateur plante avant d'afficher les résultats. Après recherche il semblerait que cela pourrait provenir de la capacité de l'environnement virtuel que j'utilise. Je vais tenter de trouver une solution lors du second Sprint. 
{% enddetails %}

### Livrables
{% details "Bases de données" %}
Les bases de données ("The Substance" et pour le bar) et les fichiers de travail intermédiaire se trouve sur le [GitHub](https://github.com/CharlesCook1/POK3).
{% enddetails %}
{% details "Résultats Analyse Sentimentale" %}
- Ci-dessous les résultats de corrélation entre les notes laissés par les spectateurs du film "The Substance" et la polarité associée à chaque commentaire.<br>
![alt text](<Images/Polarité_substance.png>)
La corrélation n'est pas évidente, lié, d'après-moi, au style du film (body horror)<br>

- Ci-après, la même corrélation pour un bar sur le Vieux Port :<br>
![alt text](<Images/Corréaltion_Bar.png>)
La corrélation est alors plus évidente, plus la note attribué par le client est proche de 5, plus la polarité attribuée par l'algorithme est proche de 1.
{% enddetails %}
{% details "Code" %}
Le code se trouve sur le [GitHub](https://github.com/CharlesCook1/POK3).
{% enddetails %}