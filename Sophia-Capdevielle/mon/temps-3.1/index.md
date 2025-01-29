---
layout: layout/mon.njk

title: "Introduction à FastAPI"
authors:
  - Sophia Capdevielle

date: 2025-01-15
temps: 3
tags:
  - fastapi

résumé: "L'objectif de ce MON est de découvrir et prendre en main FastAPI: comprendre son fonctionnement, ses avantages, et ses applications."
---

{% prerequis %}

Bases Python

{% endprerequis %}
{% lien %}

- [Introduction FastAPI](https://dev.to/ericlecodeur/introduction-a-fastapi-python-5mf)
- [Guide prise en main FastAPI et Tutoriel](https://vincent.jousse.org/blog/fr/tech/le-guide-complet-du-debutant-avec-fastapi-partie-2/)
- [Bases de FastAPI](https://jnikenoueba.medium.com/introduction-à-fastapi-les-bases-de-fastapi-509196e62d03)
- [Documentation FastAPI](https://fastapi.tiangolo.com/tutorial/)

{% endlien %}

Découverte de FastAPI et prise en main.

## Contenu

# Introduction à Fast API

FastAPI est un framework web pour la création d'API avec Python. Il est basé sur **Starlette** pour la gestion des requêtes HTTP et **Pydantic** pour la validation des données. Il est assez récent car sa première version remonte à décembre 2018.

## Installation

Il est recommandé d’utiliser un environnement virtuel pour installer toutes les dépendances nécessaires au projet.

```bash
python -m venv venv
source ./venv/bin/activate
pip install fastapi
pip install "uvicorn[standard]"
uvicorn main:app --reload
```

Dans un fichier main.py:

```python
from fastapi import FastAPI

app = FastAPI(

@app.get("/")
def root():
   return {"message": "Hello World"}
```

Ce paramétrage permet de dire : *lorsque mon application FastAPI reçoit une requête pour l'adresse `/` et la méthode HTTP `get`, exécuter la fonction `root()`.*

FastAPI propose une documentation automatique et interactive avec Swagger UI ou Redoc.

Il existe d’autres framework similaires tels que Flask ou Django REST Framework.

# Structure et fonctionnalités de base

Dans FastAPI, une **route** est une URL à laquelle on peut envoyer une requête pour récupérer ou modifier des données.

Structure de répertoires classique pour FastAPI:

apprendre-fastapi/ <-- répertoire racine de notre projet <br/>
├── app/ <-- répertoire contenant le code Python <br/>
│   ├── core/ <-- fichiers partagés (config, exceptions, …)<br/>
│   │   └── **init**.py <br/>
│   ├── crud/ <-- création, récupération, mises à jour des données <br/>
│   │   └── **init**.py <br/>
│   ├── **init**.py <br/>
│   ├── [main.py](http://main.py/) <-- point d'entrée de notre programme FastAPI <br/>
│   ├── models/ <-- les modèles de notre base de données <br/>
│   │   └── **init**.py <br/>
│   ├── schemas/ <-- les schémas de validation des modèles <br/>
│   │   └── **init**.py <br/>
│   ├── templates/ <-- fichiers html/jinja <br/>
│   ├── tests/ <-- tests <br/>
│   │   └── **init**.py <br/>
│   └── views/ <-- fonctions gérant les requêtes HTTP <br/>
│   └── **init**.py <br/>
├── public/ <-- fichiers CSS, Javascript et fichiers statiques <br/>
└── venv/ <-- environnement virtuel créé à la partie 1 <br/>

```python

app.mount("/static", StaticFiles(directory="public"), name="public")
```

On monte une route qui va répondre à l’url /static et qui servira sous cette adresse les fichiers issus du répertoire ‘public’ (directory = ‘public’), et o,n nomme cette route “public”. En gros, Si nous plaçons un fichier nommé `styles.css` dans notre répertoire `public/`, cette route va nous permettre d'y accéder par l'adresse `http://localhost:8000/public/styles.css`.

```python
templates = Jinja2Templates(directory="app/templates")

```

On créé un objet `templates` qui va nous permettre de créer de l'HTML avec le moteur de templates [Jinja2](https://jinja2docs.readthedocs.io/en/stable/). Cet objet ira chercher ses templates dans le répertoire que nous avons créé, `app/templates/`.

```python
@app.get("/")
async def root(request: Request):
    return templates.TemplateResponse(request, "home.html")
```

Notre méthode `root` récupère l'objet `request`. Cet objet est fourni par FastAPI (plus précisement par [starlette](https://www.starlette.io/), Framework sur lequel FastAPI est basé) et permet d'obtenir des informations sur la requête : l'URL d'origine, les cookies, les headers, etc. Notre méthode renvoie maintenant un objet `TemplateResponse`. C'est un objet qui va être en charge de créer du HTML à partir d'un template, `home.html` dans notre cas. Il ira chercher ce template dans le répertoire que nous avons spécifié plus haut avec `directory="app/templates"`.

## Get, Post, Put, Delete

FastAPI prend en charge les **méthodes HTTP** classiques :
| **Méthode** | **Utilisation** |
| --- | --- |
| `GET` | Lire des données |
| `POST` | Ajouter des données |
| `PUT` | Modifier des données existantes |
| `DELETE` | Supprimer des données |

```python
from fastapi import FastAPI

app = FastAPI()

@app.get("/users")
def get_users():
    return {"message": "Liste des utilisateurs"}

@app.post("/users")
def create_user(user: dict):
    return {"message": f"Utilisateur {user['name']} ajouté"}

@app.put("/users/{user_id}")
def update_user(user_id: int, new_name: str):
    return {"message": f"Utilisateur {user_id} renommé en {new_name}"}

@app.delete("/users/{user_id}")
def delete_user(user_id: int):
    return {"message": f"Utilisateur {user_id} supprimé"}

```

## Query parameters

Les paramètres de requête sont ajoutés à l’URL après `?`.

**Exemple** : `/search?query=python&limit=5`

## Path parameters

Les **path parameters** sont définis directement dans l’URL avec `{}`.

**Exemple** : `/users/42` pour récupérer l’utilisateur avec l’ID `42`.

## Swagger UI

FastAPI propose deux interfaces de documentation accessibles automatiquement :

Swagger UI : http://127.0.0.1:8000/docs

ReDoc : http://127.0.0.1:8000/redoc

## Object Relational Mapper (ORM)

- Il existe beaucoup d'ORMs différents en Python: ORM de Django, SqlAlchemy, peewee, Tortoise ORM
