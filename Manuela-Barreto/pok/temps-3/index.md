---
layout: layout/pok.njk

title: "Développement d'une Application de Suivi d'Étude avec Kotlin et Supabase"
authors:
  - Manuela BARRETO

date: 2025-03-12

temps: 3
tags:

description: Ce projet consiste à créer une application mobile similaire à Strava, mais destinée au suivi des sessions d'étude.
---

{% prerequis %}

- Connaissance de base en nocode (bubble et airtable)

{% endprerequis %}
{% lien %}

[Version teste de l'application](https://studia-47663.bubbleapps.io/version-test)

{% endlien %}

Ce projet vise à créer une application mobile pour aider les étudiants à suivre et partager leurs sessions d'étude. Les utilisateurs pourront enregistrer leurs sessions, noter leur productivité, et partager des photos et vidéos de leurs projets.

L'application **devait être créée avec Kotlin et Supabase**, en suivant une approche de développement basée sur les tests (TDD). Cependant, à la suite d'**imprévus techniques** après la première sprint, le projet a dû s'**adapter et changer d'orientation technologique**.



Le projet était structuré en deux sprints :

-   **Sprint 1** : Planification, design sur Figma, développement de l'écran de connexion et documentation initiale.

-   **Sprint 2** : Développement des autres écrans, tests utilisateurs, optimisation et finalisation.

Le premier sprint s'est déroulé comme prévu, avec un bon avancement dans la mise en place de l'interface et des bases du projet. Mais après le premier sprint, un incident majeur a impacté la progression du projet :

-   **Panne de l'ordinateur principal** : Tout le travail réalisé sous Android Studio a été perdu.

-   **Limitations matérielles** : Le seul ordinateur de secours disponible ne permettait pas d’installer des logiciels de développement comme Android Studio.

Face à ces contraintes, il était impossible de poursuivre le développement natif sous Kotlin.

Pour continuer le projet malgré ces obstacles, une nouvelle approche a été adoptée :

-   **Passage à Bubble** : Bubble, étant une plateforme de développement no-code accessible via un navigateur, a permis de continuer le développement depuis l’ordinateur de secours.

-   **Utilisation de Airtable** : Au lieu de Supabase, Airtable a été choisi pour la gestion de la base de données en raison de sa compatibilité avec Bubble.

Une fois expliqué le contexte du projet et les raisons pour lesquelles les changements étaient nécessaires, le document suivant ne parlera que du projet développé avec bubble et airtable.

## Tâches

### Sprints

#### Sprint 1

| Tâche | Durée Prévue | Durée Réel | Tâche Réalisée|
| :---: | :----: | :----------: | :--------: |
| Planification                                            | 1H                  | 0H45                | X           |
| Création du design de l'application sur figma            | 5H                  | 6H20                | X           |
| Développement de l'écran de login (refait sur bubble)                        | 3H                  | 3H                | X           |
| Documentation                                            | 1H                  | 0H30                | X           |
| **TOTAL**                                                | **10H**             | **10H35**           |             |

#### Sprint 2

| Tâche | Durée Prévue | Durée Réel | Tâche Réalisée|
| :---: | :----: | :----------: | :--------: |
| Création de la base de données airtable et intégration avec bubble            | 1H                  | 0H45                    | X            |
| Développement de l'écran "login"                          | 1H                  | 1H                    | X            |
| Développement de l'écran "recording"                       | 2H00                  | 2H45                    | X            |
| Développement de l'écran "home" (avec les posts)                                 | 4H                  | 4H                    | X            |
| Développement de l'écran "profile" (avec mes posts)                                 | 0H30                  | 0H45                    | X            |
| Documentation                                            | 1H                  |  1H15                   | X            |
| **TOTAL**                                                | **9h30**              | **10H30**                    |             |

### Horodatage

| Date | Heures passées | Indications |
| -------- | -------- |-------- |
| Jeudi 16/01     | 0H45    | Travail sur la planification                        |
| Jeudi 16/01     | 3H15    | Travail sur la création du design sur figma         |
| Vendredi 17/01  | 3H05    | Travail sur la création du design sur figma         |
| Samedi 25/01    | 3H      | Travail sur le développement de l'écran de login    |
| Mercredi 29/01  | 0H30    | Travail sur la documentation                        |
| Lundi 10/03  | 0H45    | Travail sur airtable         |
| Lundi 10/03  | 6H45    | Travail sur le développement des écrans "login","recording" et "home"                       |
| Mardi 11/03  | 1H45    | Travail sur le développement des écrans "home" et "profile"                       |
| Mercredi 12/03  | 1H15    | Travail sur la documentation                        |

## Introduction

Ce projet consiste en le développement d'une application mobile similaire à Strava, mais axée sur l'enregistrement des sessions d'étude plutôt que sur les activités sportives. Les utilisateurs pourront suivre et partager leurs sessions d'étude, favorisant ainsi une communauté engagée dans l'apprentissage.

### Technologies utilisées :
- Development de l'app : Bublle
- Base de données : Airtable
- Outil de design : Figma

---

## Premier Sprint

### Objectifs
- Planifier le projet
- Créer le design initial sur Figma
- Développer l'écran de connexion (travail perdu)
- Commencer la documentation du projet

### Défis et apprentissages
- **Planification des fonctionnalités** : Il a été difficile de définir les fonctionnalités minimales pour une première version fonctionnelle de l'application. Je me suis inspiré de Strava pour guider cette étape.

- **Design UI** : Créer un design original a été un défi, car l'influence de Strava était très présente. J'ai appris que, pour éviter des copies involontaires, il est important de chercher des références variées.

## Post-Mortem du Sprint 1

### Ce qui a bien fonctionné ✅
- La planification a été efficace et a permis un bon flux de travail.
- Le développement de l'écran de connexion a été achevé dans le délai prévu. (travail perdu)

### Points d'amélioration 🔄
- Meilleure estimation du temps pour les tâches liées au design.

### Leçons apprises 🎓
- Le design peut prendre plus de temps que prévu, il est donc important de prévoir du temps supplémentaire pour les révisions.

---

## Deuxième Sprint

### Objectifs
- Créer la base de données Airtable
- Developer les écrans sur bubble
- Créer les workflows principales pour un MVP
- Commencer la documentation du projet

### Défis et apprentissages
-   **Intégration de la base de données** : Grâce à une précédente formation sur Bubble et Airtable, l’intégration s’est déroulée sans trop de difficultés. Cependant, un point d’amélioration serait d’apprendre à relier directement les tables via Airtable, sans passer uniquement par Bubble.
-   **Développement du chronomètre** : Implémenter un chronomètre fonctionnel dans Bubble a été un défi plus complexe que prévu. Après plusieurs recherches, la solution la plus intuitive est finalement venue d’une suggestion de ChatGPT. Cet aspect montre l’importance d’explorer différentes sources d’information et de ne pas hésiter à demander de l’aide.
-   **Personnalisation avec du code** : Supprimer la barre de défilement des "repeating groups" a nécessité l’utilisation de CSS à l’intérieur de Bubble. Ce n’était pas un sujet abordé en cours, donc ce fut une belle opportunité d’apprentissage. Savoir insérer du code personnalisé dans Bubble ouvre de nouvelles possibilités pour le futur.
-   **Gestion du responsive design** : Adapter l’interface à différents écrans a été plus difficile que prévu dans Bubble, alors que cela semblait plus intuitif dans d’autres outils. Cet aspect du développement no-code nécessite donc encore plus de pratique et d’expérimentations.
-   **Optimisation et performances** : L’intégration avec Airtable a été étonnamment simple. Cependant, l’application fonctionne un peu lentement. Cette latence pourrait être due à une complexité inutile dans certaines configurations, liée à un manque d’expérience. Une phase d’optimisation sera donc nécessaire après le projet.

## Post-Mortem du Sprint 2

### Ce qui a bien fonctionné ✅
-   **Bonne gestion de la base de données Airtable** : L'intégration avec Airtable s'est avérée être une réussite, bien que j’aie encore des domaines à explorer, notamment la gestion des relations entre les tables directement dans Airtable. Le travail sur la base de données a été effectué de manière fluide et a permis de structurer l'application de manière plus simple que prévue.

-   **Développement rapide des fonctionnalités de base avec Bubble** : L'utilisation de Bubble a été très productive. J’ai pu rapidement construire les principaux écrans de l’application, y compris les écrans "login", "home" et "recording".

-   **Résolution des problèmes techniques** : Un des plus grands succès a été la capacité à résoudre rapidement les problèmes, comme la suppression de la barre de défilement des repeating groups à l’aide de CSS dans Bubble. Bien que ce ne soit pas quelque chose que j'avais vu en cours, j’ai du m’adapter et trouver une solution, ce qui a enrichi mon expérience.

-   **Travail sur le chronomètre** : Le chronomètre, qui semblait être une tâche difficile au début, a finalement été mis en place grâce à une approche innovante, que ce soit via des vidéos ou des suggestions externes comme ChatGPT.

### Points d'amélioration 🔄
-   **Optimisation des performances de l'application** : L'application est encore relativement lente, ce qui est probablement dû à l'utilisation excessive de certaines fonctionnalités dans Bubble. Une meilleure optimisation aurait pu améliorer la réactivité de l’app. Cela aurait aussi pu être évité si j'avais pris plus de temps pour comprendre les meilleures pratiques d’optimisation dans Bubble.
-   **Gestion du design responsive** : La gestion du design adaptatif s'est avérée plus difficile que prévu, ce qui a rallongé le temps de développement pour certains écrans. Cela pourrait avoir été mieux anticipé en prenant plus de temps pour expérimenter avec des configurations différentes avant de commencer à construire les interfaces finales.

### Leçons apprises 🎓
-   **Transparence dans l’estimation du temps** : Bien que les estimations de temps aient été relativement précises, il est devenu évident que certains aspects du projet, comme le responsive design et les workflows complexes, demandent plus de temps que prévu. À l’avenir, il sera important d’allouer du temps supplémentaire pour ces tâches non seulement au niveau du design mais aussi pour la mise en place des fonctionnalités.
-   **Adaptabilité aux contraintes techniques** : Comme nous l'avons vu dans les cours de méthodologie agile tout au long du semestre, il est important d'être toujours ouvert au changement. La capacité d'adaptation est une compétence non technique importante et, bien que je me sois sentie nerveuse lorsque j'ai perdu le travail que j'avais effectué précédemment, j'ai réussi à rester calme et à accepter les changements qui étaient nécessaires à la portée du projet.

-   **Importance de tester avec des utilisateurs réels** : Un point clé pour le futur est de ne pas négliger les tests utilisateurs. Bien que le sprint ait été mené seul, l'absence de retours directs sur l'application empêche d’identifier certains problèmes d’expérience utilisateur qui pourraient exister. La phase de test avec des utilisateurs réels doit devenir une priorité dans les prochaines étapes de développement.

-   **Apprentissage continu** : Le projet a été une excellente occasion d’apprendre de nouvelles techniques et d’élargir mes compétences. J’ai appris à mieux comprendre le code dans Bubble, ce qui a ouvert de nouvelles possibilités d’adaptation de l'application. Je compte continuer à expérimenter avec ces compétences afin d'optimiser l’application pour mes amis et peut-être même la publier officiellement un jour.

## Conclusion

Ce projet a été une excellente opportunité d'apprentissage, marquée par une transition imprévu du développement natif à une solution no-code avec Bubble et Airtable. Bien que des défis aient surgi, en particulier en ce qui concerne les workflows, le responsive design et les performances, j'ai pu surmonter ces obstacles et livrer une première version fonctionnelle de l'application.

Ce projet m'a également appris l'importance de l'adaptabilité face aux contraintes techniques et de l'amélioration continue. Même après la fin officielle du projet, je suis motivée à continuer à développer cette application, à optimiser ses performances et à l’enrichir avec de nouvelles fonctionnalités, tout en intégrant les retours des utilisateurs pour améliorer leur expérience.
