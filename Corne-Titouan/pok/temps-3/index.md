---
layout: layout/pok.njk

title: "Angular - Front-End Framework (2/2)"
authors:
  - Titouan Corne

temps: 3

date: 2025-01-04
tags:
  - "vert"
  - "Dev"
  - "Web"
  - "Angular"

résumé: Ce dernier POK est consacré à l'approfondissement des connaissances du language de programmation Angular. C'est la suite de mon POK2. Je vais ainsi continuer de développer le site de cuisine Miam'Miam, j'aimerais implémenter les fonctionnalités manquantes (ajout de recette, ...), mais aussi j'aimerais écrire des tests unitaires et déployer le site sur le serveur aioli (serveur de Do-It).
---

{% prerequis %}

- Connaissances du developpement web nécessaires (html, javascript, css)

{% endprerequis %}

{% lien %}

- Doc officielle : [Angular](https://angular.dev/overview)
- Mon POK 2 : [Angular - Front-End Framework (2/2)](http://localhost:8080/promos/2024-2025/Corne-Titouan/pok/temps-2/)
- [Miam'Miam](https://github.com/TitouanCorne/ApprendreAngular/tree/main/CuisineWebSite) - projet du site de cuisine.

{% endlien %}

## Cadrage

### Objectifs principaux

1. Continuer de développer le site *Miam'Miam* pour respecter le cahier des charges [POK 2]({{ site.url }}/promos/2024-2025/Corne-Titouan/pok/temps-2/).
2. Ecrire des tests pour vérifier le bon fonctionnement du site.
3. Déployer le site sur le server aioli.

### Monitoring du projet

#### Back-log et horodateur

{% details "Sprint 1" %}

- [x] Implémenter les parties manquantes du site :
  - [x] Implémenter la partie *Mes recettes*
  - [x] Implémenter la fonctionnalité permettant de mettre une recette en favoris
  - [x] Implémenter le header pour une navigation fluide et cohérente
- [x] Tester le site :
  - [x] Revoir les tests automatiquement générés par Angular
  - [x] Ajouter des tests unitaires pour valider les différentes fonctionnalités
  - [x] Créer un jeu de données de test
  - [x] Tests pour voir si l'affichage est correct (pour la page d'accueil, pour les listes de recettes et pour les points d'information)
  - [x] Tester les endpoints (GET une recette)
  - [x] Tester les filtres
    - [x] Tester le filtre *propriétaire de la recette*
    - [x] Tester le filtre *type de recette*
    - [x] Tester le filtre *barre de recherche*
    - [x] Tester plusieurs filtres en même temps

| Date | Temps passé | Commentaire |
| -------- | -------- | -------- |
| 04/01 | 2H00 | Impélmentation fonctionnalités manquantes (mes recettes) |
| 10/01 | 2H30 | Impélmentation fonctionnalités manquantes (favoris + header)|
| 18/01 | 2H30 | Suppression anciens tests + jeu de données de test + tests d'affichage |
| 19/01 | 2H00 | Tests endpoints |
| 24/01 | 2H00 | Tests filtres |

***Temps total passé sur ce sprint :*** 11H00

{% attention %}

Faire attention à ne pas sous-estimer le temps passé à coder. C'est souvent ce que j'ai tendance à faire... Pour les nouvelles fonctionnalités implémentées lors de ce sprint, je me suis mis une limite de 4h max. Mon code fonctionne mais peut être grandement amélioré ... avec plus de temps (et de pratique !!)

{% endattention %}

{% enddetails %}

{% details "Sprint 2" %}

- [x] Implémenter les parties manquantes du site :
  - [x] Implémenter une fonctionnalité permettant de gérer les utilisateurs
  - [x] Implémenter une fonctionnalité permettant à chaque utilisateur d'avoir sa propre liste de recettes favorites
  - [x] Implémenter la fonctionnalité permettant d'ajouter une recette
  - [x] Implémenter la fonctionnalité permettant de supprimer une recette
- [x] Tester le site :
  - [x] Tester *ajout d'une recette*
  - [x] Tester *suppression d'une recette*
- [x] Déployer le site sur aioli

| Date | Temps passé | Commentaire |
| -------- | -------- | -------- |
| 15/02 | 3H15 | Implémenter la fonctionnalité permettant d'ajouter une recette |
| 16/02 | 1H20 | Gestion des users + leurs recettes favorites |
| 19/02 | 2H00 | Ajouts de tests |
| 22/02 | 1H50 | Implémenter la fonctionnalité permettant de supprimer une recette |
| 22/02 | 0H45 | Amélioration CSS global |
| 08/03 | 1H00 | Déploiement sur aoili |

***Temps total passé sur ce sprint :*** 10H10

{% attention %}

Il faut savoir trouver un juste milieu en ce qui concerne les fonctionnalités à tester. Dans l'idéal, il faudrait tout tester, ce qui permettrait d'avoir une application robuste et bien documentée (car test = documentation). Mais ce n'est pas possible car on n'a pas un temps infini.

{% endattention %}

{% enddetails %}

{% faire %}

**QUOTA HORAIRE TOTAL POK 3 :** 21H10
{% endfaire %}

#### Analyse post-morterm

{% details "Sprint 1" %}

Après avoir réalisé mon MON 3.1 sur la méthodologie Test-Driven Development, j'ai été content et satisfait de voir que les connaissances acquises peuvent être facilement réutilisées. Il faut que je veille à bien documenter mon code (les tests peuvent là aussi servir), car après quelques semaines, il est difficile de se familiariser de nouveau avec du code existant.

J'ai également vu la limite de la maquette Figma (cf POK 2). Celle-ci est très pratique pour avoir une idée du rendu final. Cependant, elle ne tient pas compte de la faisabilité des fonctionnalités souhaitées. Pour illustrer cela, je peux parler du header, qui change constamment dans ma maquette (certains icônes apparaissent seulement sur des pages spécifiques). Ce header, bien que pratique sur la maquette, est affreusement compliqué, long et énervant à coder !

{% enddetails %}

{% details "Sprint 2" %}

{% enddetails %}

{% details "POK complet" %}

{% enddetails %}

## Table des matières

1. [Tester mon application](#section1)
2. [Ajout de fonctionnalités](#section2)
3. [Déploiement sur aioli](#section3)


## Tester mon application <a id="section1"></a>

Après avoir réalisé mon MON 3.1, j'ai pris conscience de l'importance des tests. J'ai donc décidé de tester mon application **Miam'Miam**.
Pour ce faire, j'ai revu chaque fichier de test de chaque composant, dans lesquels des tests de base avaient été automatiquement implémentés lors de la création du composant.

J'ai modifié ces tests pour qu'ils soient en accord avec le code déjà écrit lors de mon POK 2.

J'ai rapidement réalisé que je devais trouver une manière de tester non seulement chaque composant, mais aussi leurs interactions entre eux, notamment pour ceux qui consomment des données (présentes dans le fichier db.json).

Je me suis alors intéressé au principe de **mock**.

### Mocker un service pour les tests unitaires

En anglais **'to mock'** signifie **'simuler'**.
Dans mon application web, je dois **mocker certains services injectables** pour tester un composant.
Les composants angular sont des petites parties de code réutilisées, qui remplissent des fonctions spécifiques.
Souvent, ces composants se font injecter des services tel que **recepe-service** pour mon cas. C'est grâce à ces services que les composants accèdent aux données.
Ainsi pour tester un composant qui dispose d'un service, il faut simuler ce service (il faut le **mocker**).

Dans la documentation de [**Jasmine**](https://jasmine.github.io/tutorials/module_mocking) : *"Le module mocking est une technique de test où un test remplace partiellement ou totalement un module importé dans un autre, sans que les modules impliqués n’aient à coopérer. Dans la plupart des cas, l'injection de dépendances est une meilleure approche que le module mocking, car elle rend le code plus flexible et maintenable."*

Avantages et inconvénients du **module mocking** :

| Avantages | inconvénients |
| -------- | -------- |
| Permet de tester facilement du code fortement couplé à ses dépendances | Encourage le couplage excessif en supprimant le retour d'information des tests sur ce problème |
| Utile pour tester du code existant (*legacy code*) qui n'a pas été conçu pour être facilement testable | Modifie l'état global, rendant les tests instables (flaky) si les mocks ne sont pas réinitialisés entre les tests |
| Peut être pratique si l'on préfère utiliser des dépendances fortement intégrées (hard-wired) | Fonctionne à contre-courant du langage JavaScript en permettant à un fichier de modifier des variables globales d'un autre fichier, ce qui peut être source de confusion |
| . | Dépend souvent d'APIs instables ou de détails internes de Node, des transpileurs ou des bundlers, ce qui augmente le risque de dysfonctionnements futurs |

{% details "Exemple : comment mocker un service Angular en test unitaire avec un objet espion (spy) ?" %}

#### Création d'un service Angular (UserService)

Lorsque on "mock" un service en Angular, on simule son comportement à l'aide d'un objet espion (spy). Cela signifie qu'on remplace le service réel par un faux service qui a des méthodes contrôlées. Ces méthodes ne réalisent aucune logique réelle, mais elles retournent des résultats simulés pour le test.

```typescript
import { Injectable } from '@angular/core';

@Injectable({
  providedIn: 'root',
})
export class UserService {
  getUser() {
    return { name: 'Titouan', age: 25 };
  }
}
```

#### Création du composant utilisant ce service (UserComponent)

```typescript
import { Component } from '@angular/core';
import { UserService } from './user.service';

@Component({
  selector: 'app-user',
  template: `&lt;p&gt; &#123;&#123; user?.name &#125;&#125; (&#123;&#123; user?.age &#125;&#125 ans)&lt;/p&gt;`,
})
export class UserComponent {
  user: any;

  constructor(private userService: UserService) {}

  ngOnInit() {
    this.user = this.userService.getUser();
  }
}
```

#### Écriture du test unitaire avec un mock du service

```typescript
import { ComponentFixture, TestBed } from '@angular/core/testing';
import { UserComponent } from './user.component';
import { UserService } from './user.service';
import { of } from 'rxjs'; // Permet de créer des valeurs observables simulées

describe('UserComponent', () => {
  let component: UserComponent;
  let fixture: ComponentFixture&lt;UserComponent&gt;;
  let mockUserService: jasmine.SpyObj&lt;UserService&gt;;

  beforeEach(() =&gt; {
    // Création d’un mock du UserService
    mockUserService = jasmine.createSpyObj('UserService', ['getUser']);

    // Simulation d'une réponse du service
    mockUserService.getUser.and.returnValue({ name: 'Mocked User', age: 99 });

    TestBed.configureTestingModule({
      declarations: [UserComponent],
      providers: [{ provide: UserService, useValue: mockUserService }], // On remplace le vrai service par le mock
    }).compileComponents();

    fixture = TestBed.createComponent(UserComponent);
    component = fixture.componentInstance;
    fixture.detectChanges();
  });

  it('should display mocked user data', () => {
    // Vérifie que les données affichées sont celles du mock
    const compiled = fixture.nativeElement;
    expect(compiled.querySelector('p').textContent).toContain('Mocked User (99 ans)');
  });

  it('should call getUser() from UserService', () => {
    // Vérifie que la méthode getUser() du service a bien été appelée
    expect(mockUserService.getUser).toHaveBeenCalled();
  });
});
```

#### Explications

- On crée un "spy object" (jasmine.createSpyObj) pour simuler le UserService et on lui donne une fausse méthode getUser().
- On remplace le vrai UserService dans TestBed avec notre version mockée (useValue: mockUserService).
- On simule la réponse du service en forçant une valeur ({ name: 'Mocked User', age: 99 }).
- On teste que les valeurs affichées correspondent bien aux valeurs mockées.
- On vérifie que getUser() a bien été appelé par le composant.

{% enddetails %}

{% details "Fake Service en Angular" %}

Un **Fake Service** est une classe qui imite le vrai service, mais elle est écrite **directement dans le code du test** et **ne fait pas d'appels externes**. Son but est de **remplacer** le vrai service tout en gardant une logique réaliste.

### Création d'un service

```typescript
@Injectable({
  providedIn: 'root'
})
export class UserService {
  constructor(private http: HttpClient) {}

  getUser(): Observable&lt;User&gt; {
    return this.http.get&lt;User&gt;('https://api.example.com/user'); // Appel HTTP réel
  }
}
```

Dans un test unitaire, on ne veut pas appeler l'API, car :

- Ça rendrait les tests **lents** et instables (si l’API est en panne).
- On veut **contrôler** ce que l’API retourne pour tester différents cas.

#### Création de la classe FakeUserService dans le test

```typescript
class FakeUserService {
  getUser(): Observable&lt;User&gt; {
    return of({ name: 'Titouan', age: 24 }); // Retourne une donnée simulée
  }
}
```

Ici, on crée une classe qui imite le vrai service. La méthode getUser() retourne une fausse réponse (un *Observable* avec un utilisateur simulé). Il n'y a pas d’appel HTTP,ce qui rend le test rapide et stable.

#### Utiliser le Fake Service dans le test

Dans le fichier d'implémentation du test, on remplace UserService par FakeUserService dans le TestBed :

```typescript
TestBed.configureTestingModule({
  providers: [{ provide: UserService, useClass: FakeUserService }]
});
```

Puis on écrit les tests :

```typescript
it('should get user data', () =&gt; {
  userService.getUser().subscribe(user =&gt; {
    expect(user.name).toBe('Titouan');
    expect(user.age).toBe(25);
  });
});
//... autres tests
```

Ainsi on teste la vraie logique du composant, sans dépendre de l’API (pas d'appel => test fiable & rapide). On garde une logique réaliste, contrairement à un simple mock.

{% enddetails %}

{% info %}
Dans le cas où la structure ou la logique du service change, il faut mettre à jour le Fake Service pour qu'il reste cohérent avec le vrai service.

Mais un Fake Service **n’a pas besoin d’être aussi complet que le vrai service**. Il doit juste fournir les fonctionnalités nécessaires aux tests.
{% endinfo %}
Mais comme nous l'explique la documentation de Jasmine, les mocks ont leur limite... En effet avec les mocks, les tests deviennent trop dépendants des implémentations internes. Si on change la structure du service, il faudra aussi mettre à jour tous les mocks.

## Ajout de fonctionnalités <a id="section2"></a>

### Implémentation du component Header

Comme expliqué dans mon POK2, j'ai dans un premier temps créé une maquette figma pour avoir une image du rendu final vers lequel je voulais me diriger. Dans un second temps, j'ai codé mon application Angular en suivant les caractéristiques de la maquette. Cependant, pour le **Header**, j'ai décidé de ne plus suivre la maquette, car ce que j'avais dessiné sur Figma n'était vraiment pas facile à mettre en place du point de vue du code.

C'est à ce moment-là que j'ai compris qu'il est réellement important d'avoir un point de vue critique sur ce qu'on imagine sur Figma. Il faut que ce soit simple et facile à coder.

Ainsi, j'ai créé un unique Header qui ne dépend pas de la page visitée et qui reste valide pour chacune d'entre elles. Ce Header est divisé en deux parties :

1. Le logo de l'application qui permet de retourner rapidement au menu.
2. La div contenant les icônes : une icône (flèche) pour revenir à la page précédente et une icône (+) pour ajouter une nouvelle recette

### Gestion des utilisateurs et des recettes favorites

Ce site se veut d'être un site familial, sans aucune donnée sensible. Ainsi, j'ai trouvé inutile de coder un système de log in classique avec identifiant + mot de passe. J'ai seulement inséré une dropdown list accessible à la première page qui permet de choisir le bon utilisateur.

Derrière ce système de gestion d'utilisateurs, j'ai créé une seconde interface (`ng generate interface Users`) et un service dédié aux users (`ng generate service Users`). Ce service expose des méthodes permettant notamment de savoir quel est l'utilisateur actuellement sélectionné, et ce, quelle que soit la page visitée.

Ensuite, j'ai ajouté un nouveau champ pour mes objets de type *Recepe*. Ce champ, dénommé *favorite*, est un tableau de *boolean* de longueur 5 (car il y a 5 utilisateurs). Ce tableau, propre à chaque recette, permet de retrouver les utilisateurs ayant cette recette en favoris. Lorsqu'on crée une nouvelle recette, et qu'on est donc propriétaire de cette dernière, cette recette est automatiquement placée dans les favoris.

### Implémentation de méthodes pour supprimer/ajouter une recette

Comme expliqué précédemment, le *Header* expose une icône *"plus"* (+) pour ajouter une nouvelle recette. Pour cela, j'ai créé un nouveau composant *newRecepe*, qui est associé à une nouvelle route. Ce composant affiche un formulaire permettant de saisir toutes les informations nécessaires à la création d'une nouvelle recette.

Pour cela, j'ai utilisé `NgForm` et `FormsModule`. Je vous invite à aller voir ça sur mon [GitHub]("https://github.com/TitouanCorne/ApprendreAngular/tree/main/CuisineWebSite/src/app/new-recepe") (fichiers new-recepe.component.html & new-recepe.component.ts) si ça vous intéresse ;)

Ensuite, j'ai implémenté la fonctionnalité permettant de supprimer une recette. Cette fonctionnalité peut être utilisée seulement pour les recettes dont l'user est propriétaire.

## Déploiement sur aioli <a id="section3"></a>

Après avoir build mon application, j'ai compressé mon dossier de build (dist) et ma base de donnée (db.json).

Puis à l'aide de la commande `scp .\mon_dossier_compresse.tar basilic@aioli.ec-m.fr:`, j'ai copié ces dossiers compressé à la racine de mon espace de travail sur le serveur distant aioli. Une fois les dossier dézippés (`tar -xvf mon_fichier.tar`), il a fallu executer le build de mon application (`npm run start`) sur le port 1104, qui correspond, pour basilic, au port servi par nginx et également lancer le service de base de données.
