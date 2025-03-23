---
layout: layout/pok.njk

title: "POK 3 : Suite site Web en React pour gérer mes tâches"
authors:
  - Kévin BERNARD

date: 2025-01-07

tags:
  - "temps 3"
  - "vert"
  - "React"
  - "3D"
  - "Gestion de tâches"
  - "Spring Boot"
  - "Spring Data JPA"
  - "API REST"
  - "React Three Fiber"
  - "Aioli"

description: Un POK où je crée un site web attirant en React pour gérer mes tâches avec des animations 3D.
---

{% prerequis %}
Pas de prérequis pour le moment
{% endprerequis %}

{% lien %}
<b>SOURCES</b>

- [Vidéo Youtube de The Ethical Technologist, The Best Way To Style Components In React | CSS Modules](https://www.youtube.com/watch?v=i63WQrzrKag)
- [Vidéo Youtube de Roberts Dev Talk, Javascript Promises vs Async Await EXPLAINED (in 5 minutes)](https://www.youtube.com/watch?v=li7FzDHYZpc)
- [Vidéo Youtube de Web Dev Simplified, Why I Don’t Use Arrow Functions With const/let](https://www.youtube.com/watch?v=5iGGvJn8K1U)
- [Vidéo Youtube de Web Dev Simplified, Asynchronous Vs Synchronous Programming](https://www.youtube.com/watch?v=Kpn2ajSa92c)
- [GitHub du site, creature_site de KevinBERNARD1901](https://github.com/KevinBERNARD1901/creature_site)

{% endlien %}

{% chemin %}
<b> POK & MON </b>
- [POK 2 : Site Web en React pour gérer mes tâches, Kévin BERNARD](../temps-2/index.md/)
{% endchemin %}

Le but de ce POK est de réaliser un site en React pour gérer mes tâches avec un horodateur, un agenda avec une importation de créatures 3D à partir de Blender.

## Tâches

### Sprints

#### Sprint 1

- [x] Changer l'image de fond
- [] Faire la page de To do (liste des tâches, ajout de tâches, suppression de tâches, chronomètre, marquer comme fait, catégoriser par domaine et par réalisation)
- [x] Rajouter les requêtes API pour les tâches

#### Sprint 2

- [x] Migrer le back sur le serveur aioli
<!-- Changer les get pour les tâches par réalisation et par domaine ou un seul get et filtrer dans le front-->
- [x] Faire le front la partie front de To do

### Horodatage

| Date | Heures passées | Indications |
| -------- | -------- |-------- |
| **Début Sprint 1** |
| Mardi 07/01 | 2H | Ce que je fais en Front + mise en place d'une image en background |
| Vendredi 10/01 | 4H30 | Faire les hooks/appel à l'API + étude fonction fetch + await/async VS then + fonction arrow vs function + sync vs async |
| Samedi 18/01 | 2H | Connection back-front et création méthode post |
| Lundi 20/01 | 2H | Création de Domain.java + Implementation des méthodes HTTP de TO DO (suppression de tâches, chronomètre, marquer comme fait, catégoriser par domaine et par réalisation) |
| Total | 10H30 |
| **Début Sprint 2** |
|Jeudi 30/01 | 1H40 | Création des éléments du model dans le back |
|Jeudi 06/03 | 3H30 | Clone du git sur Aioli et lancement sur le port 1102 + installation de maven et jdk + essaie d'installation de sqlite, mysql|
| Vendredi 07/03 | 2H10 | Modification de la page to_do, centralisation des hooks |
| Dimanche 09/03 | 2H20 | addTasks qui marche et useEffect qui marche avec les fonctions que l'on crée dans le hook |
| Total | 9H40 |

## Contenu

### Premier Sprint

#### Changement de l'image de fond

Dans un premier temps, je voulais avoir un aperçu de ce que donnerais la page finale avec un décor en background donc j'ai importé une image en background issue de Pinsterest, [Image ajouté par Agatha de Lima](https://fr.pinterest.com/pin/10977592835947395/).

J'avais un souci quand je mettais l'image en fond d'écran parce que le RouterProvider faisait en sorte de s'adapter à la taille de mes composants ce qui empêchait l'image d'être en fond d'écran.

Pour corriger cela j'ai défini mes bodys, html, #root comme étant en 100% de la hauteur et de la largeur.

#### Faire la page de To do

##### Connection back-front et création méthode get

Pour connecter mon front à mon back, j'ai utilisé la fonction fetch qui permet de faire des requêtes HTTP. J'aurais pu utiliser Axios mais je ne souhaitais pas apprendre une librairie pour le moment.

Pour intégrer la fonction fetch, j'ai dû apprendre à utiliser les fonctions async et await que j'ai comparé avec then. J'ai regardé une vidéo de [Roberts Dev Talk](https://www.youtube.com/watch?v=li7FzDHYZpc) qui explique la différence entre les promesses et les fonctions async et await.

Ensuite j'ai dû apprendre les différences entre les fonctions fléchées et les fonctions normales parce que j'avais des problèmes avec les fonctions fléchées notamment avec les variables const et let.
J'ai regardé une vidéo de [Web Dev Simplified](https://www.youtube.com/watch?v=5iGGvJn8K1U) qui explique pourquoi il ne faut pas utiliser les fonctions fléchées avec const et let.

J'ai enfin pu créer une méthode post pour créer une tâche dans ma base de données et j'ai pu appelé la méthode get dans mon front, c'est là que j'ai créé le composant Task.js.

##### Création de Domain.java + Implementation des méthodes HTTP de TO DO

J'avais déjà créé la méthode post pour créer une tâche et get pour avoir la liste des tâches.
J'ai donc créé les méthodes delete et patch pour marquer une tâche comme faite, supprimer une tâche, ajouter le temps passé sur cette tâche et catégoriser par domaine et par réalisation.

Pour cela, j'ai d'abord ajouté les attributs (à partir du diagramme de classe de mon [POK 2](../temps-2/index.md)) :

```java
    private LocalTime timePassedOnIt;
    private LocalTime totalTime;
    private Date creationDate;
    private Date doneDate;
    @ManyToOne
    @JoinColumn(name = "domainId")
    private Domain projectDomain;
```

Pour les domaines, j'ai créé une classe Domain.java qui contient un domainId, name, domainDone, creationDate, doneDate et color. Ensuite j'ai ajouté un attribut projectDomain dans Task.java qui est une clé étrangère vers Domain avec un ManyToOne et un JoinColumn pour spécifier le nom de la colonne.

J'ai rajouté mes méthodes patch et delete dans mon TaskController.java et j'ai pu les appeler dans mon front. Sachant que PatchTaskTime_passed_on_it ajoute la durée envoyée en paramètre à la durée déjà passée sur la tâche et PatchTaskTotal_time remplace la durée totale par la durée envoyée en paramètre.

{% details "Code" %}

```java
// DeleteMapping
    @DeleteMapping("/tasks/{taskId}")
    public void deleteTaskByID(@PathVariable int taskId) {
        taskService.deleteById(taskId);
    }

    // PatchMapping
    @PatchMapping("/tasks/taskDone/{taskId}")
    public void PatchTaskTaskDone(@PathVariable int taskId) {
        taskService.patchTaskTaskDone(taskId);
    }

    @PatchMapping("tasks/timePassedOnIt/{taskId}")
    public void PatchTaskTime_passed_on_it(@PathVariable int taskId, @RequestParam LocalTime timePassedOnIt) {
        taskService.PatchTaskTime_passed_on_it(taskId, timePassedOnIt);
    }

    @PatchMapping("tasks/totalTime/{taskId}")
    public void PatchTaskTotal_time(@PathVariable int taskId, @RequestParam LocalTime totalTime) {
        taskService.patchTaskTotal_time(taskId, totalTime);
    }
```

{% enddetails %}

J'ai également mis plusieurs routes get pour récupérer les tâches par réalisation et par domaine. Je n'ai pas encore réfléchi s'il vaut mieux par exemple: faire une route pour chaque domaine ou une route pour tous les domaines et filtrer dans le front.

### Second Sprint

#### Finalisation du model du backend

Dans mon backend, j'ai fini mon model et les relations entre mes classes.

#### Migration du back sur le serveur Aioli

J'ai d'abord cloné le git sur Aioli et j'ai lancé le serveur sur le port 1102.

Comme je n'avais pas Maven et le Java sur Aioli, j'ai dû les installer.
Je n'avais pas les droits suffisants pour simplement les installer avec apt-get donc je les ai installé manuellement.

J'ai télécharger le tar.gz sur mon ordinateur et l'ai envoyé sur Aioli avec la commande scp.
Il ne restait plus qu'à décompresser le fichier et à ajouter les variables d'environnement dans le fichier .bashrc.

J'avais un souci avec la base de données, je n'arrivais pas à installer sqlite3 et mysql et le tar.gz de la base de données ne fonctionnait pas. Donc pour éviter de ne passer que du temps sur ça, j'ai décidé de continuer le développement de mon frontend.

J'ai trouver les commandes dans le cours de Linux.

#### Développement de la partie front de To do

J'ai modifié la page de To do pour qu'elle soit plus jolie et plus fonctionnelle. J'ai centralisé les hooks dans un fichier hooks.js pour que ce soit plus lisible et plus facile à modifier.

J'avais un souci parce que j'essayais d'utiliser mes hooks dans mon useEffect, pour résoudre le problème je retourne des fonctions dans mes hooks et je les appelle dans mon useEffect.

J'ai eu le temps de faire la fonction addTasks, le getTasks et l'affichage des tâches.

Je me suis documenté sur Stack Overflow pour les problèmes d'utilisation de hooks dans useEffect.

### Retour sur expérience

**Difficultés :**

- Installation de Maven et du JDK sur Aioli
- Installation de SQLite3 et MySQL sur Aioli
- Utilisation de hooks dans useEffect

**Bilan**

Pour le sprint 1, je voulais initialement me concentrer sur le frontend mais j'ai fait plus de backend. Je suis un peu dessus mais j'ai vraiment bien pris en main Sring.
Pour le sprint 2, je me suis rendu compte que je ne peux pas avancer sur mon frontend sans un Mockup final.

De manière globale, je réalise mieux l'importance du Mockup et je pense pouvoir dire que j'ai les bases de Spring Boot.