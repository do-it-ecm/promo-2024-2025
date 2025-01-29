---
layout: layout/pok.njk

title: "Développement d'une Application de Suivi d'Étude avec Kotlin et Supabase"
authors:
  - Manuela BARRETO

date: 2025-03-12

temps: 3
tags:

résumé: Ce projet consiste à créer une application mobile similaire à Strava, mais destinée au suivi des sessions d'étude.
---

{% prerequis %}

- Connaissance de base en programmation Kotlin
- Expérience avec Android Studio
- Compréhension des principes de TDD
- Notions de base en gestion de bases de données et utilisation de Supabase

{% endprerequis %}
{% lien %}

[Introduction à Supabase](https://do-it.aioli.ec-m.fr/promos/2024-2025/Manuela-Barreto/mon/temps-3.1/)

{% endlien %}

Ce projet vise à créer une application mobile pour aider les étudiants à suivre et partager leurs sessions d'étude. Les utilisateurs pourront enregistrer leurs sessions, noter leur productivité, et partager des photos et vidéos de leurs projets. L'application sera développée en utilisant Kotlin et Supabase, avec une approche de développement basée sur les tests (TDD).

## Tâches

### Sprints

#### Sprint 1

| Tâche | Durée Prévue | Durée Réel | Tâche Réalisée|
| :---: | :----: | :----------: | :--------: |
| Planification                                            | 1H                  | 0H45                | X           |
| Création du design de l'application sur figma            | 5H                  | 6H20                | X           |
| Développement de l'écran de login                        | 3H                  | 3H                | X           |
| Documentation                                            | 1H                  | 0H30                | X           |
| **TOTAL**                                                | **10H**             | **10H35**           |             |

#### Sprint 2

| Tâche | Durée Prévue | Durée Réel | Tâche Réalisée|
| :---: | :----: | :----------: | :--------: |
| Développement des autres écrans                          | 5H                  |                     |             |
| Publication et Testes Utilisateurs                       | 2H                  |                     |             |
| Débogage et Optimisation                                 | 2H                  |                     |             |
| Documentation                                            | 1H                  |                     |             |
| **TOTAL**                                                | **10**              |                     |             |

### Horodatage

Toutes les séances et le nombre d'heure que l'on y a passé.

| Date | Heures passées | Indications |
| -------- | -------- |-------- |
| Jeudi 16/01     | 0H45    | Travail sur la planification                        |
| Jeudi 16/01     | 3H15    | Travail sur la création du design sur figma         |
| Vendredi 17/01  | 3H05    | Travail sur la création du design sur figma         |
| Samedi 25/01    | 3H      | Travail sur le développement de l'écran de login    |
| Mercredi 29/01  | 0H30    | Travail sur la documentation                        |

## Introduction

Ce projet consiste en le développement d'une application mobile similaire à Strava, mais axée sur l'enregistrement des sessions d'étude plutôt que sur les activités sportives. Les utilisateurs pourront suivre et partager leurs sessions d'étude, favorisant ainsi une communauté engagée dans l'apprentissage.

L'objectif principal est d'acquérir une expérience pratique dans le développement d'applications mobiles dotées d'une base de données structurée et mise à jour en temps réel. De plus, ce projet vise également à me permettre d'apprendre concrètement la méthodologie Test-Driven Development (TDD).

### Technologies utilisées :
- Langage : Kotlin
- IDE : Android Studio
- Base de données : Supabase (avec intégration via supabase-kt)
- Outil de design : Figma

Le projet est divisé en deux sprints. Le premier sprint a été achevé et s'est concentré sur la planification, le design de l'interface et l'implémentation initiale de la connexion.

---

## Premier Sprint

### Objectifs
- Planifier le projet
- Créer le design initial sur Figma
- Développer l'écran de connexion
- Commencer la documentation du projet

### Défis et apprentissages
- **Planification des fonctionnalités** : Il a été difficile de définir les fonctionnalités minimales pour une première version fonctionnelle de l'application. Je me suis inspiré de Strava pour guider cette étape.

- **Design UI** : Créer un design original a été un défi, car l'influence de Strava était très présente. J'ai appris que, pour éviter des copies involontaires, il est important de chercher des références variées.

- **Utilisation de Supabase** : L'application des connaissances acquises durant le MON3.1 a été utile pour consolider mon apprentissage sur les bases de données en temps réel.

---

## Post-Mortem du Sprint 1

### Ce qui a bien fonctionné ✅
- La planification a été efficace et a permis un bon flux de travail.
- Le développement de l'écran de connexion a été achevé dans le délai prévu.

### Points d'amélioration 🔄
- Meilleure estimation du temps pour les tâches liées au design.

### Leçons apprises 🎓
- Le design peut prendre plus de temps que prévu, il est donc important de prévoir du temps supplémentaire pour les révisions.
- Documenter les petites décisions tout au long du processus aide à assurer la continuité du projet.

---

## Conclusion

Ce projet constitue une excellente opportunité d'apprentissage sur le développement mobile, les bases de données en temps réel et le TDD. Le prochain sprint sera essentiel pour consolider les acquis et finaliser une première version fonctionnelle de l'application.

En plus de l'apprentissage technique, j'ai également pris conscience de l'importance d'une bonne planification du design et de la nécessité de rechercher des inspirations variées afin d'éviter des références trop marquantes.
