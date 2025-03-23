---
layout: layout/mon.njk

title: "Programmation orienté objet avec python"
authors:
  - Baptiste Audouin

date: 2025-01-28
temps: 3
tags:

description: "Dans ce MON je souhaite découvrir la programmation orienté objet avec Python."

---

{% prerequis %}

- Bases en python

{% endprerequis %}
{% lien %}

- [Formation Youtube](https://www.youtube.com/watch?v=Y-wXK0Wu5pc)
- [Github - Python-Machine-Learning - 09-POO](https://github.com/MachineLearnia/Python-Machine-Learning/blob/master/09%20-%20Programmation%20Orientée%20Objet.ipynb)
- [Documentation officielle python](https://docs.python.org/3/tutorial/classes.html)
- [Real Python - Object-Oriented Programming in Python](https://realpython.com/python3-object-oriented-programming/)

{% endlien %}

Ce MON présente la programmation orientée objet (POO) en Python. Dans ce MON on parle des éléments clés de la programmation orienté objet comme les classes, les objets, l’encapsulation, l’héritage et le polymorphisme. A la fin de ce MON il y a une petite application concrête avec un gestionnaire de bibliothèque.

## Contenu

### Introduction
La programmation orientée objet (POO) est un modèle de programmation qui repose sur le concept d'objets. Un objet est une instance d'une classe, qui regroupe des attributs (données) et des méthodes (fonctions). La POO permet d'organiser et de structurer le code de manière plus modulaire et réutilisable.

#### Pourquoi utiliser la POO ?

- **Modularité** : Facilite la gestion et la modification du code.
- **Réutilisation** : Possibilité de réutiliser les classes dans plusieurs programmes.
- **Encapsulation** : Protège les données et limite les interactions directes.
- **Extensibilité** : Permet d'étendre les fonctionnalités sans modifier le code existant.

### Principes fondamentaux

#### 1. Classes et Objets

Une classe est un modèle permettant de créer des objets. Un objet est une instance d'une classe.

```python
class Voiture:
    def __init__(self, marque, modele):
        self.marque = marque
        self.modele = modele

    def afficher_info(self):
        return f"Voiture: {self.marque} {self.modele}"

ma_voiture = Voiture("Tesla", "Model 3")
print(ma_voiture.afficher_info())
```
Après execution, voici ce que le script renvoie :
```
Voiture: Tesla Model 3
```

#### 2. Encapsulation

L'encapsulation limite l'accès direct aux attributs d'un objet ce qui permet de sécuriser celui-ci.

```python
class CompteBancaire:
    def __init__(self, solde):
        self.__solde = solde

    def deposer(self, montant):
        self.__solde += montant

    def afficher_solde(self):
        return f"Votre solde est de: {self.__solde}€"

compte = CompteBancaire(1000)
compte.deposer(500)
print(compte.afficher_solde())
```

Après execution, voici ce que le script renvoie :
```
Votre solde est de 1500€
```

#### 3. Héritage

L'héritage permet à une classe d'hériter des propriétés et méthodes d'une autre classe.

```python
class Animal:
    def __init__(self, nom):
        self.nom = nom

    def parler(self):
        pass

class Chien(Animal):
    def parler(self):
        return "Woof!"

class Chat(Animal):
    def parler(self):
        return "Miaou!"

chien = Chien("Rex")
chat = Chat("Mia")
print(chien.parler())
print(chat.parler())
```

Après execution, voici ce que le script renvoie :
```
Woof!
Miaou!
```

#### 4. Polymorphisme
Le polymorphisme permet d'utiliser une même interface pour différentes classes.

```python
def faire_parler(animal):
    print(animal.parler())

faire_parler(chien)
faire_parler(chat)
```

Après execution, le script renvoie bien le même chose que précédemment :

```
Woof!
Miaou!
```

### Application pratique : Gestion d'une Bibliothèque

Nous allons créer un système simple de gestion de livres dans une bibliothèque. On va donc créer une bibliothèque dans laquelle on va ajouter des livres et donner la possibilité, s'il est disponible de l'emprunter.

```python
class Livre:
    def __init__(self, titre, auteur):
        self.titre = titre
        self.auteur = auteur
        self.disponible = True

    def emprunter(self):
        if self.disponible:
            self.disponible = False
            return f"Vous avez emprunté {self.titre}"
        return f"{self.titre} n'est pas disponible"

    def retourner(self):
        self.disponible = True
        return f"Vous avez retourné {self.titre}"

class Bibliotheque:
    def __init__(self):
        self.livres = []

    def ajouter_livre(self, livre):
        self.livres.append(livre)

    def afficher_livres(self):
        for livre in self.livres:
            statut = "disponible" if livre.disponible else "emprunté"
            print(f"{livre.titre} de {livre.auteur} - {statut}")

# Application
biblio = Bibliotheque()
livre1 = Livre("1984", "George Orwell")
livre2 = Livre("Le Petit Prince", "Antoine de Saint-Exupéry")

biblio.ajouter_livre(livre1)
biblio.ajouter_livre(livre2)
biblio.afficher_livres()

print(livre1.emprunter())
biblio.afficher_livres()
```

Voici ce qui est renvoyé dansle terminal :
````
1984 de George Orwell - disponible
Le Petit Prince de Antoine de Saint-Exupéry - disponible
Vous avez emprunté 1984
1984 de George Orwell - emprunté
Le Petit Prince de Antoine de Saint-Exupéry - disponible
````

## Conclusion
Dans ce projet, nous avons exploré les bases de la programmation orientée objet en Python en abordant ses principes fondamentaux : classes, encapsulation, héritage et polymorphisme. Nous avons également appliqué ces concepts à un exemple concret de gestion d'une bibliothèque.
