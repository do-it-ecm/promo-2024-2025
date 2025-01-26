---
layout: layout/pok.njk

title: "Développement d'une application de gestion des tâches avec PyQt"
authors:
  - Serigne Mbaye Sy AMAR

date: 2024-16-12

temps: 3
tags:
- PyQt
- Qt
- Python
- SQLite

résumé: Ce POK vise à créer une application graphique de gestion des taches avec PyQt, où je vais apprendre à concevoir une interface utilisateur, y intégrer une base de données SQLite pour gérer des données dynamiques Personnaliser l'apparence avec des styles QSS.
---

{% prerequis %}

- Une bonne base en python
- Base en SQL

{% endprerequis %}
{% lien %}

- [MON de Duc](https://cumin.aioli.ec-m.fr/promos/2023-2024/Dang-Vu-Duc/mon/temps-1.1/) 
- [POK de Duc](https://cumin.aioli.ec-m.fr/promos/2023-2024/Dang-Vu-Duc/pok/temps-1/) 

{% endlien %}


### Objectifs principaux  

1. **Créer une interface utilisateur avec PyQt**, permettant la gestion de tableaux et de cartes dynamiques.  

3. **Implémenter la base de données SQLite** pour assurer la conservation des données entre les sessions.  

4. **Ajouter du design** à l’aide de QSS pour la personnalisation des interfaces.  

---  

### Recueil des besoins  

{% details "Détails du recueil des besoins" %}  

| Étape                          | Résultat attendu                                                                                 | Difficultés rencontrées                                                                                       |
|--------------------------------|--------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------|
| **Identification personnelle des besoins** | Définir les fonctionnalités principales en tant qu'utilisateur (ajout de tableaux, gestion des cartes). | Risque de vouloir tout intégrer dès le départ et de dépasser le cadre d’un projet MVP (produit minimum viable). |
| **Analyse des outils existants**          | Étudier Trello et d’autres outils similaires pour s’inspirer des fonctionnalités essentielles. | Difficulté à rester focalisé sur les fonctionnalités indispensables sans ajouter des options superflues.       |
| **Étude des contraintes techniques**      | Vérifier si les outils techniques choisis (par exemple PyQt et SQLite) peuvent répondre efficacement aux besoins. | Découverte des limites techniques comme la gestion des performances avec des widgets complexes sous PyQt.     |
| **Prototypage rapide**                    | Concevoir une interface simple et fonctionnelle pour tester rapidement mes idées.                          | Adapter rapidement les designs en fonction des tests et des ajustements nécessaires.                          |

{% enddetails %} 

 

{% note %}  

Les fonctionnalités minimales identifiées incluent la gestion de tableaux dynamiques et la possibilité d’ajouter et modifier des cartes associées.  

{% endnote %}  

#### Fondements  


- Je veux une interface simple, sans besoin de connexion à un serveur distant.  

- La gestion des cartes et des tableaux doit rester rapide et réactive.  

- Le design doit être uniforme.

---  

### Monitoring du projet  

#### Back-log et organisation par sprints  

Chaque sprint répond à une **question principale**.  


### Sprint 1 : **Comment utiliser PyQt pour créer une interface fonctionnelle ?**  

**Objectifs :**  

1. Étudier PyQt et comprendre ses composants de base.  

2. Concevoir une interface simple permettant de visualiser des tableaux.  

3. Commencer l’intégration de styles via QSS.  

**Backlog :**  

- [x] Lire les POK et MON de Duc ainsi que documentation officielle de PyQt et effectuer des exercices pratiques.  

- [x] Développer une maquette avec des `QVBoxLayout` pour organiser les tableaux.  

- [x] Créer un premier prototype fonctionnel permettant d’afficher des widgets dynamiquement.  

- [x] Étudier et intégrer des styles basiques avec QSS.  

{% details "Détails des activités du Sprint 1" %}  

| Date       | Heures passées | Indications                                   |
|------------|----------------|-----------------------------------------------|
| 16/01/2025 | 3.0h           | Lecture et exercices sur PyQt (widgets de base). |
| 16/01/2025 | 1.5h           | Exploration des styles via QSS.              |
| 17/01/2025 | 2.0h           | Design des tableaux avec QVBoxLayout.        |
| 18/01/2025 | 1.5h           | Étude des signaux et slots.                  |
| 18/01/2025 | 2.0h           | Création de l'interface principale.          |


**Total du sprint 1 :** 10h.  

{% enddetails %}  

#### Activités réalisées  

1. **Étude et expérimentation des composants de PyQt**  

 Découverte des **widgets** et de leur rôle dans la construction d'interfaces graphiques.  

 **Widgets étudiés sont** :  

- `QWidget`  qui est le conteneur de base.  

- `QPushButton` qui sont les boutons interactifs.  

- `QLabel` qui affiche les textes et les images.  

 **Objectif :** Comprendre comment assembler ces widgets pour structurer une interface.  

{% details "Exemple - Création de widgets de base" %}  

Voici comment configurer un bouton et un label dans une interface :  

```python  

button = QPushButton("Cliquez-moi")  

label = QLabel("Bienvenue dans PyQt")  

layout = QVBoxLayout()  

layout.addWidget(button)  

layout.addWidget(label)  

widget.setLayout(layout)  

```  

Ce code crée une fenêtre simple avec un bouton et un label empilés verticalement.  

{% enddetails %}  

1. **Création d’un layout structuré pour afficher des tableaux**  

- Utilisation de `QHBoxLayout` pour organiser les widgets horizontalement (exemple : plusieurs tableaux).  

- Mise en place d’un **conteneur** qui permet d’ajouter ou de supprimer des widgets.  

{% details "Exemple - Organisation de widgets avec QHBoxLayout" %}  

```python  

layout = QHBoxLayout()  

button1 = QPushButton("Tableau 1")  

button2 = QPushButton("Tableau 2")  

layout.addWidget(button1)  

layout.addWidget(button2)  

widget.setLayout(layout)  

```  

Chaque bouton représente un tableau dans l’interface utilisateur.  

{% enddetails %}  

1. **Gestion des événements utilisateur avec les signaux et slots**  

- Connexion des actions utilisateur aux fonctions Python via des **signaux**.  

 Exemple : Ajouter un tableau lorsqu’un bouton est cliqué.  

{% details "Exemple - Connexion d’un bouton à une action" %}  

```python  

button.clicked.connect(self.ajouter_tableau)  

def ajouter_tableau(self):  

print("Un nouveau tableau a été ajouté !")  

```  

Lorsque le bouton est cliqué, la fonction `ajouter_tableau` est déclenchée.  

{% enddetails %}  

1. **Apprentissage et application des styles QSS**  

- Utilisation de QSS pour personnaliser l’apparence des boutons, labels, et arrière-plans.  

- Définition d’un fichier `main.qss` pour centraliser les styles.  

{% details "Exemple - Stylisation avec QSS" %}  

Fichier QSS pour personnaliser un bouton :  

```css  

QPushButton {  

background-color: #0079BF;  

color: white;  

border-radius: 5px;  

}  

QPushButton:hover {  

background-color: #026AA7;  

}  

```  

Le bouton change de couleur lorsque la souris passe dessus.  

{% enddetails %}  

---  

{% details "Ce que j'ai appris avec PyQt et les layouts" %}  

1. **Composants de base PyQt :**  

- **QWidget**, le composant de base pour créer une fenêtre ou un conteneur.  

- **QHBoxLayout**,  permet d’organiser les widgets horizontalement, ce qui est idéal pour une interface basée sur des ligne, comme Trello.  

- **QPushButton** et **QLabel**, utilisés pour les interactions utilisateur de base.  

2. **Gestion des layouts :**  

- Si on utilise un `QVBoxLayout` imbriqué dans un `QHBoxLayout`, on peut organiser efficacement des colonnes dynamiques, par exemple pour afficher des listes de cartes sous forme de tableaux.  

- Les marges et les espacements (`setContentsMargins`, `setSpacing`) permettent d'ajuster précisément l'apparence.  

3. **Signaux et slots :**  

- Les signaux comme `clicked` permettent de connecter un bouton à une action spécifique.  

- Les slots facilitent la gestion des interactions sans complexifier le code.  

**Ressources utilisées :**  

- **POK et Mon de Duc** pour comprendre comment structurer les interfaces de manière modulaire (lien au niveau des sources).  

- **Vidéos YouTube sur PyQt** pour les démonstrations pratiques des layouts et widgets (lien, voir la partie sources).  

{% enddetails %}  

---  

### Analyse post-mortem  

- **Points forts :** Maîtrise des bases de PyQt et de QSS, premier prototype fonctionnel.  

- **Points faibles :** Temps sous-estimé pour la personnalisation des styles.  

- **Amélioration :** Prévoir un temps supplémentaire pour ajuster le design.  

{% info "Objectif clé réussi" %}
   Comprendre comment organiser et structurer une interface graphique avec PyQt.
   {% endinfo %}

   {% note %} Les connaissances acquises dans ce sprint serviront de base pour intégrer des fonctionnalités dans les sprints futurs. {% endnote %}

---


{% details "Livrable du sprint 1" %}  

La page de connexion:

![image](./bienv.png) 

La première page:

![image](./inte.png) 

{% enddetails %}  

 ## Sources :
{% lien %}
- [Documentation officielle PyQt ](https://doc.qt.io/qtforpython-6/)
- [MON de Duc](https://cumin.aioli.ec-m.fr/promos/2023-2024/Dang-Vu-Duc/mon/temps-1.1/) 
- [POK de Duc](https://cumin.aioli.ec-m.fr/promos/2023-2024/Dang-Vu-Duc/pok/temps-1/) 
- [PyQt5 tutorial - login Form](https://www.youtube.com/watch?v=SfeqGZ_x9kc)
{% endlien %}
<!-- 
### Sprint 2 : **Comment intégrer une base de données SQLite et gérer les événements utilisateur ?**  

**Objectifs :**  

1. Implémenter une base de données SQLite pour persister les données des tableaux et cartes.  

2. Permettre la création, suppression et modification des tableaux par l’utilisateur.  

3. Intégrer une gestion des cartes dans chaque tableau.  

**Backlog :**  

- [x] Configurer SQLite pour stocker les données des tableaux et cartes.  

- [x] Ajouter des fonctionnalités pour créer, supprimer et modifier des tableaux.  

- [x] Gérer les cartes dynamiquement dans les tableaux.  

- [x] Finaliser les styles QSS pour uniformiser l’expérience utilisateur.  

- [ ] Implémenter des tests pour vérifier la cohérence des données.  

{% details "Détails des activités du Sprint 2" %}  

| Date | Heures passées | Indications |  

|--------------|----------------|-----------------------------------------------|  

| 19/01/2025 | 2.0h | Configuration de la base SQLite. |  

| 20/01/2025 | 2.5h | Gestion dynamique des tableaux. |  

| 21/01/2025 | 3.0h | Gestion des cartes dans les tableaux. |  

| 22/01/2025 | 2.5h | Tests unitaires et ajustements des styles. |  

**Total du sprint 2 :** 10h.  

{% enddetails %}  

**Réponse à la question :**  

{% details "Ce que j'ai appris avec SQLite et les événements utilisateur" %}  

1. **Base de données SQLite :**  

- Créer une table pour les tableaux (`CREATE TABLE boards`) et une table pour les cartes associées (`CREATE TABLE cards`).  

- Utilisation des relations entre tableaux et cartes via une clé étrangère (`board_id` dans la table `cards`).  

- Gestion des opérations CRUD (Create, Read, Update, Delete) pour manipuler les données dynamiquement.  

2. **Gestion des signaux et événements utilisateur :**  

- Utilisation des signaux `clicked` pour connecter les boutons d’ajout et suppression aux actions correspondantes.  

- Implémentation de slots personnalisés pour mettre à jour l'interface et la base de données simultanément.  

3. **Stylisation via QSS :**  

- Amélioration de l’esthétique de l’application avec des styles comme :  

```css  

QPushButton {  

background-color: #0079BF;  

color: white;  

border-radius: 3px;  

}  

QPushButton:hover {  

background-color: #026AA7;  

}  

```  

- Simplification du design en regroupant les styles dans un fichier unique `main.qss`.  

**Ressources utilisées :**  

- **POK et Mon de Duc** pour structurer la gestion des données dans un projet logiciel.  

- **Vidéos YouTube sur SQLite avec PyQt** pour la configuration des bases de données.  

{% enddetails %}  

{% attention %}  

Lors de la suppression d’un tableau, il est important de supprimer également toutes les cartes associées dans la base de données pour éviter les incohérences.  

{% endattention %}  

---  

### Analyse post-mortem  

#### Sprint 1  

- **Points forts :** Maîtrise des bases de PyQt et de QSS, premier prototype fonctionnel.  

- **Points faibles :** Temps sous-estimé pour la personnalisation des styles.  

- **Amélioration :** Prévoir un temps supplémentaire pour ajuster le design.  

#### Sprint 2  

- **Points forts :** Bonne avancée dans la gestion des données et la persistance avec SQLite.  

- **Points faibles :** La gestion des cartes a été plus complexe que prévu.  

- **Amélioration :** Intégrer des tests unitaires dès le début pour détecter les incohérences.  

---  

### Livrable final  

{% details "Fonctionnalités principales" %}  

1. **Gestion des tableaux** : Ajouter, modifier et supprimer des tableaux.  

2. **Gestion des cartes** : Ajouter, déplacer et supprimer des cartes dans les tableaux.  

3. **Persistance des données** : Les données sont stockées dans une base SQLite.  

4. **Interface personnalisée** : Utilisation de QSS pour un design moderne et uniforme.  

{% enddetails %}  

---  

### Conclusions méthodologiques  

1. **Prototypage rapide** : Le recours à un prototype initial a permis d’identifier rapidement les problèmes techniques.  

2. **Planification par sprints** : Décomposer le projet en sprints avec des questions précises a permis de garder le cap sur les objectifs.  

3. **Documentation continue** : Noter les décisions techniques et les problématiques rencontrées a simplifié l’intégration des fonctionnalités.  

{% note %}  

Les retours utilisateurs après le premier prototype ont été très utiles pour affiner le design et les fonctionnalités principales.  

{% endnote %}  

---  

### Pistes d'amélioration  

- Automatiser les tests pour éviter des bugs liés à la gestion des événements utilisateur.  

- Explorer davantage les fonctionnalités avancées de PyQt comme les animations ou les graphiques.  

- Ajouter une fonctionnalité de "drag and drop" pour déplacer les cartes entre les tableaux.  

---  

Si vous avez d'autres éléments spécifiques à inclure ou des détails à approfondir, faites-le-moi savoir ! 

---  

### Sprint 1 : **Créer une interface fonctionnelle et ergonomique avec PyQt**  

**Durée :** 10 heures  

**Objectifs spécifiques :**  

1. Étudier et comprendre les concepts fondamentaux de PyQt.  

2. Créer une interface de base pour afficher les tableaux.  

3. Apprendre et intégrer les styles QSS pour personnaliser l’apparence.  

---  



### Sprint 2 : **Ajouter une base de données SQLite et gérer les interactions**  

**Durée :** 10 heures  

**Objectifs spécifiques :**  

1. Ajouter une base de données SQLite pour stocker les données des tableaux et cartes.  

2. Créer des fonctionnalités d’ajout, suppression, et modification.  

3. Synchroniser les données entre l’interface utilisateur et la base de données.  

---  

#### Activités réalisées  

1. **Configuration de SQLite pour stocker les données (2 heures)**  

- Création de deux tables : une pour les tableaux (`boards`) et une pour les cartes associées (`cards`).  

{% details "Exemple - Structure des tables SQLite" %}  

- **Table des tableaux** :  

```sql  

CREATE TABLE boards (  

id INTEGER PRIMARY KEY,  

title TEXT NOT NULL  

);  

```  

- **Table des cartes** :  

```sql  

CREATE TABLE cards (  

id INTEGER PRIMARY KEY,  

title TEXT NOT NULL,  

board_id INTEGER,  

FOREIGN KEY (board_id) REFERENCES boards (id)  

);  

```  

Les deux tables sont liées par la clé étrangère `board_id`.  

{% enddetails %}  

2. **Connexion entre PyQt et SQLite (3 heures)**  

- Utilisation de `sqlite3` pour interagir avec la base de données.  

- Insertion et récupération des données dynamiquement.  

{% details "Exemple - Insérer des données dans SQLite" %}  

```python  

conn = sqlite3.connect('database.db')  

cursor = conn.cursor()  

cursor.execute("INSERT INTO boards (title) VALUES (?)", ("Tableau 1",))  

conn.commit()  

conn.close()  

```  

Ce code insère un tableau nommé "Tableau 1" dans la base de données.  

{% enddetails %}  

3. **Gestion des événements utilisateur (2 heures)**  

- Implémentation d’une fonction pour afficher dynamiquement les tableaux depuis SQLite.  

- Chaque tableau est représenté par un bouton.  

{% details "Exemple - Charger les tableaux depuis SQLite" %}  

```python  

def charger_tableaux(self):  

self.layout.clear() # Nettoyer le layout  

tableaux = self.db.get_boards() # Récupérer les tableaux depuis SQLite  

for tableau in tableaux:  

bouton = QPushButton(tableau['title']) # Créer un bouton pour chaque tableau  

self.layout.addWidget(bouton) # Ajouter le bouton au layout  

```  

Les tableaux sont affichés dynamiquement en fonction des données présentes dans SQLite.  

{% enddetails %}  

4. **Finalisation des styles et tests (3 heures)**  

- Ajustement des styles pour les rendre cohérents.  

- Tests des fonctionnalités principales (ajout, suppression, et modification).  

{% details "Exemple - Personnalisation avancée avec QSS" %}  

```css  

QPushButton#delete-button {  

background-color: #EB5A46;  

color: white;  

}  

QPushButton#delete-button:hover {  

background-color: #CF513D;  

}  

```  

Le style distingue visuellement les boutons de suppression des autres actions.  

{% enddetails %}  

---  

### Analyse finale  

#### Points forts :  

1. PyQt a permis une création rapide d'une interface graphique fonctionnelle.  

2. SQLite a facilité la gestion et la persistance des données.  

3. Les styles QSS ont amélioré l’apparence de l’application.  

#### Points faibles :  

1. Le temps consacré à l’apprentissage des signaux et slots a été légèrement sous-estimé.  

#### Pistes d’amélioration :  

- Ajouter des tests unitaires pour valider automatiquement les fonctionnalités.  

- Explorer des fonctionnalités avancées de PyQt, comme le **drag-and-drop** pour déplacer les cartes entre les tableaux.  

--- 

  -->