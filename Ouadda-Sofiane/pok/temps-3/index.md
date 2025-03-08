---
layout: layout/pok.njk
title: "Poésie Learn - App"
authors:
  - Sofiane Ouadda
date: 2025-02-22

tags:
  - 'Mobile'
  - 'React Native'
  - 'Apprentissage'
  - 'Poésie'

résumé: "J'ai voulu apprendre à développer une application mobile. J'ai donc décidé de développé une application mobile interactive pour l'apprentissage de poésies via des méthodes interactives telles que flashcards et fill-in-the-blanks, intégrant la répétition espacée."
---

{% prerequis %}

**Niveau :** Basique à Intermédiaire  
**Pré-requis :**
- Connaissances de base en React Native et JavaScript.
- Notions de gestion d'état en React.

{% endprerequis %}

{% lien %}

- [GitHub Projet Poésie Learn](https://github.com/SofianeOuadda/poesie-learn)
- [Documentation React Native](https://reactnative.dev/docs/getting-started)
- [Documentation Expo](https://docs.expo.dev/)

{% endlien %}

# POK 3 - Poésie Learn - App

Ce POK décrit les étapes de développement d'une application mobile interactive dédiée à l'apprentissage de poésies. L'utilisateur pourra sélectionner un poème et s'exercer via des exercices interactifs (flashcards et fill-in-the-blanks) en s'appuyant sur une logique de répétition espacée pour améliorer la mémorisation.

## Objectifs principaux

1. **Acquérir et consolider des compétences en développement mobile React Native** au travers d’un projet concret.  
2. **Permettre un apprentissage interactif des poésies** via des exercices dynamiques (flashcards, fill-in-the-blanks, etc.).  
3. **Offrir une interface utilisateur intuitive** pour sélectionner un poème et suivre sa progression.


## Plan d'action

### 1. Conception et préparation
- Définir précisément les fonctionnalités essentielles du MVP.
- Choisir l’outil de développement (React Native CLI ou Expo).
- Créer le dépôt Git et configurer l’environnement de développement sur Mac.
- Élaborer un schéma d’architecture de l’application et préparer des maquettes simples des écrans.

### 2. Développement de l’interface utilisateur
- **Création des écrans principaux :**
  - **Accueil (HomeScreen.js) :** Présentation de l’app, explication rapide du fonctionnement et accès aux sections principales.
  - **Sélection de Poème (PoemSelectionScreen.js) :** Affichage d’une liste de poésies avec titres et extraits.
  - **Exercice d’Apprentissage (ExerciseScreen.js) :** Écran interactif proposant l’exercice (flashcard ou fill-in-the-blanks).
- **Navigation :** Intégrer React Navigation pour permettre une navigation fluide entre les écrans.
- **Design et ergonomie :** Soigner l’apparence et la clarté des écrans pour garantir une bonne expérience utilisateur.

### 3. Implémentation de la méthode interactive
- **Mode Flashcard :**
  - Créer un composant dédié `Flashcard.js` pour afficher une ligne ou un couplet du poème.
  - Permettre à l’utilisateur de saisir ou de rappeler la ligne suivante et vérifier sa réponse via un bouton de validation.

- **Mode Fill-in-the-Blank :**
  - Créer un composant `FillInBlank.js` pour afficher le poème avec certains mots remplacés par des champs à compléter.
  - Implémenter une logique de vérification des réponses et fournir un feedback visuel immédiat.

- **Répétition espacée :**
  - Enregistrer les erreurs et les passages mal mémorisés.
  - Mettre en place une logique simple pour proposer plus fréquemment les passages erronés, en ajustant ainsi la révision de l’utilisateur.

### 4. Tests, débogage et finalisation
- **Tests fonctionnels :** Vérifier manuellement le fonctionnement de chaque écran et de chaque interaction.
- **Correction des bugs :** Identifier et résoudre les problèmes rencontrés pour assurer la stabilité de l’app.
- **Validation finale :** S’assurer de la cohérence entre les différents modes d’exercice et de la fluidité de la navigation.
- **Démo locale :** Préparer une démonstration fonctionnelle du MVP à lancer sur l’iOS Simulator ou l’Android Emulator sur Mac.
- **Tests de performance avancés :** Quelques tests automatisés ont été écourtés faute de temps.

## Architecture complète du projet

L'architecture du projet est organisée de la manière suivante :

```
PoésieLearnApp/
├── App.js                 # Point d'entrée de l'application
├── assets/               
│   ├── images/
│   └── fonts/
├── components/            # Composants réutilisables
│   ├── Flashcard.js
│   ├── FillInBlank.js
│   ├── Header.js
│   └── Footer.js
├── navigation/            # Configuration de la navigation
│   └── AppNavigator.js
├── screens/               # Écrans principaux de l'application
│   ├── HomeScreen.js
│   ├── PoemSelectionScreen.js
└── └── ExerciseScreen.js
```



## Sprints de développement

### Sprint 1 : Planification et configuration (~5h)
- [x] **Définir le périmètre du MVP** et les fonctionnalités indispensables.  
- [x] **Initialiser le projet avec Expo** :  

  ```bash
  npx expo init PoésieLearnApp
  ``` 

- [x] Créer le dépôt Git et configurer l’environnement de développement sur Mac.  
- [x] Élaborer un schéma d’architecture complet et préparer des maquettes pour les écrans.  

- **Livrables :**  
  - [x] Projet initialisé avec la structure vierge.  
  - [x] Maquettes et schéma de l’application.  

---

### Sprint 2 : Création de l’interface utilisateur (~6h)

Après avoir initialisé le projet, j'ai commencé à **remplir le code** :

- [x] **Développer les écrans de base :**  
  - `HomeScreen.js` (Accueil)  
  - `PoemSelectionScreen.js` (Sélection de Poème)  
  - `ExerciseScreen.js` (Exercice d’Apprentissage)  

- [x] **App.js :** Fichier principal qui englobe la navigation.

```javascript
// App.js
import React from 'react';
import { NavigationContainer } from '@react-navigation/native';
import AppNavigator from './navigation/AppNavigator';

export default function App() {
  return (
    <NavigationContainer>
      <AppNavigator />
    </NavigationContainer>
  );
}
```

- [x] **Intégrer React Navigation** via un fichier navigation/AppNavigator.js :

```javascript
// navigation/AppNavigator.js
import React from 'react';
import { createStackNavigator } from '@react-navigation/stack';
import HomeScreen from '../screens/HomeScreen';
import PoemSelectionScreen from '../screens/PoemSelectionScreen';
import ExerciseScreen from '../screens/ExerciseScreen';

const Stack = createStackNavigator();

export default function AppNavigator() {
  return (
    <Stack.Navigator initialRouteName="Home">
      <Stack.Screen name="Home" component={HomeScreen} />
      <Stack.Screen name="PoemSelection" component={PoemSelectionScreen} />
      <Stack.Screen name="Exercise" component={ExerciseScreen} />
    </Stack.Navigator>
  );
}
```
- [x] **Design et ergonomie** : j'ai stylisé les écrans avec `StyleSheet` (React Native) pour optimiser la lisibilité.

- ~~[ ] **Tests d’affichage** sur l’émulateur iOS/Android pour valider le rendu.~~

- **Livrables** :

  - [x] Écrans fonctionnels et navigation opérationnelle.
  - [x] Interface testée sur l’émulateur.


### Sprint 3 : Implémentation de la méthode interactive (~6h)

- [x] **Mode Flashcard** :
  - Création de `Flashcard.js` pour afficher une ou plusieurs lignes du poème et permettre la validation de l’utilisateur.

```javascript
// components/Flashcard.js
import React, { useState } from 'react';
import { View, Text, TextInput, Button, StyleSheet } from 'react-native';

export default function Flashcard({ line, onValidate }) {
  const [userInput, setUserInput] = useState('');

  return (
    <View style={styles.container}>
      <Text style={styles.lineText}>{line}</Text>
      <TextInput
        style={styles.input}
        value={userInput}
        onChangeText={setUserInput}
        placeholder="Votre réponse..."
      />
      <Button title="Valider" onPress={() => onValidate(userInput)} />
    </View>
  );
}

const styles = StyleSheet.create({
  container: {
    marginVertical: 10,
    padding: 10,
  },
  lineText: {
    fontSize: 16,
    marginBottom: 5,
  },
  input: {
    borderColor: '#ccc',
    borderWidth: 1,
    padding: 8,
    marginBottom: 10,
    borderRadius: 4,
  },
});
```

- [x] **Mode Fill-in-the-Blank** :
  - [x] Création de `FillInBlank.js` pour afficher le poème avec des mots cachés.

- [x] **Répétition espacée** :
  - Mise en place de fonctions utilitaires dans `utils/spacedRepetition.js` pour stocker et gérer le nombre d’erreurs.

- **Livrables** :
  - [x] Composants `Flashcard` et `FillInBlank` opérationnels.
  - ~~[ ] Logique de répétition espacée testée et validée.~~


### Sprint 4 : Tests, débogage et finalisation (~3h)
- [x] Tests fonctionnels approfondis sur l’ensemble de l’application.

- [x] Correction des bugs et refonte de certains aspects UX.

- ~~[ ] Tests de performance avancés : plusieurs tests automatisés prévus ont été écourtés, faute de temps.~~

- ~~[ ] Préparer la démo locale : lancement sur l’iOS Simulator/Android Emulator pour présenter le MVP.~~

- **Livrables** :
  - ~~[ ] Application stable et fonctionnelle.~~
  - ~~[ ] Démo prête à être présentée en local, sans déploiement sur l’App Store.~~


## Horodateur

| Date   | Heures passées | Indications                                                                                 |
|--------|----------------|---------------------------------------------------------------------------------------------|
| 22/02  | 2H             | Planification, définition du périmètre et création du dépôt Git                             |
| 22/02  | 3H             | Initialisation du projet (Expo), configuration de l’environnement et préparation des maquettes |
| 01/03  | 4H             | Développement des écrans UI (Accueil, Sélection de Poème) et intégration de la navigation   |
| 02/03  | 4H             | Implémentation des modes Flashcard et Fill-in-the-Blank avec intégration du feedback        |
| 05/03  | 4H             | Développement de la logique de répétition espacée et premiers tests fonctionnels           |
| 06/03  | 3H             | Tests, débogage, finalisation du MVP et préparation de la démo (èchec)                |
