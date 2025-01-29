---
layout: layout/pok.njk

title: "Scaling et CI/CD du site Do-It"
authors:
  - Loïck Goupil-Hallay

date: 2024-12-20

temps: 3

tags:
  - "devops"
  - "scaling"
  - "gitops"

résumé: Rework du site Do-It pour apporter la possibilité de scaling et l'utilisation de GitHub Actions pour le CI/CD.
---

{% sommaire %}
[[toc]]
{% endsommaire %}

{% prerequis '**POK avancé**'%}
- [Git](https://git-scm.com/)
- [Eleventy](https://www.11ty.dev/)
- [Bash](https://www.gnu.org/software/bash/)
- [Nginx](https://www.nginx.com/)
{% endprerequis %}

{% lien '**Liens utiles**' %}
- [POK Arthur Louradou Git Submodules pour Do-It]({{ site.url }}/promos/2024-2025/Louradou-Arthur/pok/temps-1bis/creation_sous_repo_git/)
{% endlien %}

## Introduction

Après 3 ans de bons et loyaux services, le site Do-It arrive à saturation. Il est en effet gangréné par les **mauvaises pratiques** qui se sont **accumulées** au fil des POK & MON. Il est temps de reprendre les choses en main et de revoir l'architecture du site pour le rendre scalable et plus facile à maintenir.

Le build a dépassé la taille du Giga, le **déploiement** via GitHub Actions **ne passe plus entièrement** à cause de cela, et les pauvres élèves se font engueuler par nos chers professeurs car ils ne peuvent pas consulter leurs rendus.

## Problèmes actuels

### Taille du build

Le site Do-It est construit avec Eleventy, et au fil des POK & MON, **la taille du build a explosé**. Il est maintenant impossible de déployer le site en entier via GitHub Actions, car **le build dépasse la taille maximale supportée par GitHub Pages**. Cela est dû au contenu multimédia (images, vidéos, sons, diaporamas, zip, code source,...) qui a été ajouté au fil des années en les plaçant directement dans le dossier `src`.

La limite de taille du build est de **1 Go** pour GitHub Pages, et le site Do-It dépasse largement cette taille.

### Scaling

Le repository Git servant à build le site est **monolithique**. Tous les élèves ont leur propre dossier dans le dossier `src`, et le site est construit en entier à chaque modification. Cela pose plusieurs problèmes :
- **Pas de gestion fine des droits** : les élèves ont accès à tout le site, ce qui peut entraîner des modifications non désirées
- **Temps de build trop long** : plus il y a d'élèves, plus le temps de build augmente
- **Performances Git dégradées**: GitHub recommande de ne pas excéder 5Gb de données par repository sous peine de faire face à de sérieux problèmes de performance, celui de Do-It atteint les 4.1Gb à l'heure actuelle. La siuation est critique.

### Mauvaises pratiques

Le site Do-It est victime de **mauvaises pratiques** en cascade:
- **Les médias sont directement au niveau des markdown** : cela augmente la taille du build et rend le site difficile à maintenir
- **Les promos ne respectent pas toutes le même format**: la nomenclature des directories et des fichiers n'est pas vérouillée. Cela rend pénible la maintenance du site
- **Les chemins des médias sont en dur dans les fichiers HTML** : cela rend difficile la migration des médias vers un autre emplacement
- **Les noms de directories et de fichiers comportent des caractères spéciaux** : cela peut poser des problèmes de compatibilité avec certains systèmes de fichiers et avec les scripts de build
- **Les élèves ont accès à tout le site** : cela peut entraîner des modifications non désirées et des conflits
- **Personne n'utilise Git**: Les élèves ne font pas l'effort d'utiliser Git comme il faut, tout le monde push sur la branche `main` et je reçois régulièrement des messages pour résoudre des problèmes de conflits.

## Objectifs

- **Résoudre le problème de taille de build** pour que toutes les actions de déploiement passent
- **Permettre le scaling du site** pour supporter un nombre croissant d'élèves
- **Imposer des bonnes pratiques** pour éviter de retomber dans les travers actuels
- **Ajouter des fonctionnalités front-end** pour améliorer l'expérience utilisateur (plugins, rework graphiques, résumés,...)
- **Migrer le site sur notre propre serveur aioli** pour éviter les limitations de GitHub Pages
- **Mettre en place du GitOps** pour faciliter le déploiement et la maintenance du site

## Rework

### Résolution de la taille du build

Le problème d'échec de déploiement étant urgent, j'ai décidé de le résoudre immédiatement en **réencodant** toutes les images du site en **WebP** et toutes les vidéos en **MP4** avec le **codec H.264**. Cela a permis de **diviser par 2 la taille du build** et de permettre le déploiement complet du site via GitHub Actions.

{% details "Script bash d'optimisation des médias" %}
Ce script permet de réencoder les images en WebP, les vidéos en MP4 et les audios en Opus. Il permet également de mettre à jour les références des médias dans les fichiers HTML et de réécrire l'historique Git pour supprimer les médias originaux.

```bash
#!/bin/bash

if [[ "$1" == "--rewrite-git-history" ]]; then
    REWRITE_GIT_HISTORY=true
    shift
fi

if [[ "$1" == "-h" || "$1" == "--help" ]]; then
    echo "Usage: optimizer.bash <image|video|audio>"
    echo "Optimize media files in the current directory."
    exit 0
fi

temp_file=$(mktemp) # Temporary file to store paths for git filter-repo

if [[ "$1" == "image" || "$2" == "image" || "$3" == "image" ]]; then
    # Process image files (JPG, JPEG, PNG)
    find src -type f \( -name "*.jpg" -o -name "*.jpeg" -o -name "*.png" -o -name "*.JPG" -o -name "*.JPEG" -o -name "*.PNG" \) -print0 | while IFS= read -r -d '' img; do
        ffmpeg -y -i "$img" -q:v 75 "${img%.*}.webp" && \
        echo "$img" >> "$temp_file" && \
        rm "$img"

        if [[ "$REWRITE_GIT_HISTORY" == "true" ]]; then
             git rm --cached "$img"
        fi
    done

    # Update image references in HTML files
    find src -type f -name "*.md" -exec sed -i \
        -e '/http/! s/\.png/\.webp/g' \
        -e '/http/! s/\.PNG/\.webp/g' \
        -e '/http/! s/\.jpg/\.webp/g' \
        -e '/http/! s/\.JPG/\.webp/g' \
        -e '/http/! s/\.jpeg/\.webp/g' \
        -e '/http/! s/\.JPEG/\.webp/g' {} +

elif [[ "$1" == "video" || "$2" == "video" || "$3" == "video" ]]; then
    # Process video files (MP4, MOV, MKV)
    find src -type f \( -name "*.mp4" -o -name "*.mov" -o -name "*.mkv" \) -print0 | while IFS= read -r -d '' video; do
        ffmpeg -y -i "$video" -c:v libx264 -preset veryslow -c:a aac -b:a 96k "${video%.*}.compressed.mp4" && \
        echo "$video" >> "$temp_file" && \
        rm "$video" && \
        mv "${video%.*}.compressed.mp4" "${video%.*}.mp4"

        if [[ "$REWRITE_GIT_HISTORY" == "true" ]]; then
             git rm --cached "$video"
        fi
    done

    # Update video references in HTML files
    find src -type f -name "*.md" -exec sed -i \
        -e '/http/! s/\.mp4/\.compressed\.mp4/g' \
        -e '/http/! s/\.mov/\.compressed\.mp4/g' \
        -e '/http/! s/\.mkv/\.compressed\.mp4/g' {} +


elif [[ "$1" == "audio" || "$2" == "audio" || "$3" == "audio" ]]; then
    # Process audio files (WAV, FLAC, MP3, OGG)
    find src -type f \( -name "*.wav" -o -name "*.flac" -o -name "*.mp3" -o -name "*.ogg" \) -print0 | while IFS= read -r -d '' audio; do
        ffmpeg -y -i "$audio" -c:a libopus -b:a 96k "${audio%.*}.opus" && \
        echo "$audio" >> "$temp_file" && \
        rm "$audio"

        if [[ "$REWRITE_GIT_HISTORY" == "true" ]]; then
             git rm --cached "$audio"
        fi
    done

    # Update audio references in HTML files
    find src -type f -name "*.md" -exec sed -i \
        -e '/http/! s/\.wav/\.opus/g' \
        -e '/http/! s/\.flac/\.opus/g' \
        -e '/http/! s/\.mp3/\.opus/g' \
        -e '/http/! s/\.ogg/\.opus/g' {} +

else
    echo "Usage: optimizer.bash <image|video|audio>"
    exit 1
fi

# Rewrite git history for all stored paths
if [[ -s "$temp_file" && "$REWRITE_GIT_HISTORY" == "true" ]]; then
    git filter-repo --invert-paths --paths-from-file "$temp_file" --force
fi

# Cleanup temporary file
rm "$temp_file"
```
{% enddetails %}

Ce script a permis de réduire la taille du build à **600Mo**, ce qui était suffisant pour permettre le déploiement complet du site.\
**Cependant**, laisser perdurer la situation actuelle **condamnerait** la promotion suivante à subir les mêmes problèmes. Il est donc nécessaire de **revoir l'architecture du site** pour le rendre viable.

La solution perenne est de **sortir les médias du build** et de les stocker dans un **serveur dédié**.\
Comme ni vous, ni moi n'avons envie de payer ou de maintenir un serveur, la solution la plus simple est de **continuer d'utiliser GitHub** pour stocker les médias, mais de **ne plus les inclure dans le build**. Nous allons simplement **référencer les médias** dans les fichiers HTML et les laisser **accessibles via GitHub**.

Pour faire cela, on utilise un **script de build** qui va **réécrire les URLs des médias** pour qu'ils pointent vers le **serveur GitHub**.\

{% details "Script de build pour réécrire les URLs des médias" %}
Ce script de build permet de réécrire les URLs des médias pour qu'ils pointent vers le serveur GitHub.\
{% raw %}
```js
if (process.env.NODE_ENV === "production") {

  // DO NOT REMOVE THOSE CONSTANTS,
  // PERFORMING A GIT REMOTE -V OPERATION ON EACH FILE IS TOO EXPENSIVE
  // HARDCODED VALUES ARE FINE IN OUR CONTEXT

  // Raw GitHub URL constants
  const RAW_GITHUB_BASE = "https://raw.githubusercontent.com";
  // Repositories owner
  const GITHUB_REPO_OWNER = "do-it-ecm";
  // Regex to match promo paths (and extract the promo year and relative path)
  const IS_PROMO_PATH = /src\/promos\/(\d{4}-\d{4})(\/?.*)?/;
  // Regex to match the CS paths (and extract the relative path)
  const IS_CS_PATH = /src\/cs\/(.*)/;
  // Commit ref to use for all submodules
  const COMMIT_REF = "refs/heads/main"; // Don't bother finding the commit ref for each submodule, just use main

  function mediaUrlTransform(context) {
    const urlsOptions = {
      eachURL: function (url, attr, tagName) {
        let remoteUrl = url;
        if (url.includes("://")) {
          // Don't transform external URLs
        } else { // Hopefully valid relative URL
          const baseDir = process.cwd();
          let absoluteDirPath = "";
          if (url.startsWith("/")) {
            url = url.slice(1);
            absoluteDirPath = path.dirname(path.resolve(baseDir, "src", url));
          } else {
            absoluteDirPath = path.dirname(path.resolve(baseDir, path.dirname(context.inputPath), url));
          }
          const promoMatch = absoluteDirPath.match(IS_PROMO_PATH);
          if (promoMatch) {
            // Promo path
            const promoYear = promoMatch[1];
            // Retrieve relative path (remove trailing slash)
            const relativePath = promoMatch[2] ? promoMatch[2].replace(/\/$/, "") : "";
            remoteUrl = `${RAW_GITHUB_BASE}/${GITHUB_REPO_OWNER}/promo-${promoYear}/${COMMIT_REF}/${relativePath}/${path.basename(url)}`;
          } else {
            const csMatch = absoluteDirPath.match(IS_CS_PATH);
            if (csMatch) {
              // CS path
              const relativePath = csMatch[1];
              remoteUrl = `${RAW_GITHUB_BASE}/${GITHUB_REPO_OWNER}/courses/${COMMIT_REF}/${relativePath}/${path.basename(url)}`;
            } else {
              const relativePath = path.relative(baseDir, absoluteDirPath);
              remoteUrl = `${RAW_GITHUB_BASE}/${GITHUB_REPO_OWNER}/do-it/${COMMIT_REF}/${relativePath}/${path.basename(url)}`;
            }
          }

        }
        return remoteUrl;
      },
      filter: {
        img: { src: true, srcset: true },
        video: { src: true, srcset: true },
        audio: { src: true },
        source: { src: true, srcset: true }
      }
    };
    return urls(urlsOptions);
  }
  eleventyConfig.htmlTransformer.addPosthtmlPlugin("html", mediaUrlTransform, { priority: -1 });
} else {
  console.warn("Skipping media URL transform in development mode");
}
```
{% endraw %}
{% enddetails %}

### Scaling

Pour permettre le scaling du site, il faut impérativement **séparer les promotions**. Chaque promotion doit avoir son propre repository Git, et le site doit être construit à partir de **repositories séparés**. Cela permettra de **réduire le temps de build** et de **séparer les droits et les préoccupations**.

Concrètement, chaque promotion aura son propre repository Git, et le site Do-It sera construit à partir de **submodules Git**.\
Les submodules Git permettent d'inclure un repository Git dans un autre repository Git. Cela permet de **garder les repositories séparés** tout en **les incluant dans un repository parent**.

Cela passe par plusieurs étapes clés:
- **Création d'une organisation GitHub Do-It** pour stocker les repositories des promotions et le repository du site Do-It
- **Création de teams GitHub** pour gérer les droits des élèves sur les repositories
- **Création d'un repository par promotion** pour stocker les fichiers des élèves (réalisé par Arthur)
- **Création d'un repository pour le site Do-It** pour référencer les repositories des promotions et stocker la logique de build
- **Mise en place de submodules Git** pour inclure les repositories des promotions dans le repository du site Do-It

### Mauvaises pratiques

#### Script

Pour résoudre les problèmes de mauvaise pratiques, j'ai décidé de mettre en place des scripts (javascript) qui s'assurent de la **conformité du code**. Vous pouvez consulter les scripts de vérification de conformité dans [{{ site.source }}/tree/main/scripts/compliance/]({{ site.source }}/tree/main/scripts/compliance/).

Ces scripts vérifient que:
- Les fichiers et répertoires ont des noms standards, composés uniquement de caractères alphanumériques, de tirets / underscores et de points. Cela évite de créer des erreurs dans les scripts de réécriture des URLs des médias.
- La structure du dossier élève est respectée, avec un fichier index.(md|njk|html) si du contenu est présent.
- Les médias sont stockés dans des répertoires dédiés (`assets`) et non directement à côté des fichiers markdown.

#### Pipeline CI/CD

En plus, j'ai ajouté une **pipeline CI/CD** GitHub Actions qui va **vérifier** que chacune des nouvelles pratiques est respectée, et dans le cas contraire, le **build ne se lance pas**.

{% details "Pipeline CI/CD Compliance GitHub Actions" %}
Cette pipeline GitHub Actions utilise du caching pour accélérer le build et lance tous nos tests de conformité.\
Elle ne se lance que lorsqu'une merge request est acceptée ou lorsqu'un submodule est mis à jour. Finito les push sur `main`!

```yaml
{% raw %}
name: check-compliance

on:
  repository_dispatch:
    types: [submodule-update]
  pull_request:
    types:
      - closed
    branches:
      - main

env:
  NODE_VERSION: "20.7" # Define the Node.js version here

jobs:
  check-compliance:
    runs-on: ubuntu-latest
    steps:
      # Checkout code without initializing submodules
      - uses: actions/checkout@v4
        with:
          submodules: false # Defer submodule initialization

      # Restore Git Submodules Cache
      - name: Restore Git Submodules Cache
        uses: actions/cache@v4
        with:
          path: .git/modules
          key: submodules-${{ github.ref_name }}
          restore-keys: |
            submodules-${{ github.ref_name }}
            submodules-

      # Git Submodule Update
      - name: Git Submodule Update
        run: |
          git submodule sync
          git submodule update --init --recursive
          git submodule foreach "git fetch origin main && git reset --hard origin/main"

      # Cache Git Submodules
      - name: Cache Git Submodules
        uses: actions/cache@v4
        with:
          path: .git/modules
          key: submodules-${{ github.ref_name }}

      # Restore Node.js Modules Cache
      - name: Restore Node.js Modules Cache
        uses: actions/cache@v4
        with:
          path: ~/.npm
          key: npm-cache-${{ env.NODE_VERSION }}-${{ github.ref_name }}
          restore-keys: |
            npm-cache-${{ env.NODE_VERSION }}-${{ github.ref_name }}
            npm-cache-${{ env.NODE_VERSION }}-
            npm-cache-

      # Use Node.js
      - name: Use Node.js ${{ env.NODE_VERSION }}
        uses: actions/setup-node@v4
        with:
          node-version: ${{ env.NODE_VERSION }}

      # Install dependencies
      - name: Install dependencies
        run: npm ci

      # Save Node.js Modules Cache
      - name: Save Node.js Modules Cache
        uses: actions/cache@v4
        with:
          path: ~/.npm
          key: npm-cache-${{ env.NODE_VERSION }}-${{ github.ref_name }}

      - name: Check Compliance
        run:  npm run check-compliance
{% endraw %}
```
{% enddetails %}

{% details "Pipeline CI/CD Publish GitHub Actions" %}
Cette pipeline GitHub Actions construit le site Do-It à partir des submodules Git et applique les changements sur la branche `gh-pages` pour déployer le site. Elle ne conserve que la dernière version du build pour éviter de faire grossir le repository Git inutilement.

```yaml
{% raw %}
name: publish

on:
  workflow_run:
    workflows: ["check-compliance"]
    types:
      - completed

env:
  NODE_VERSION: "20.7" # Define the Node.js version here

jobs:
  publish:
    if: ${{ github.event.workflow_run.conclusion == 'success' }}
    runs-on: ubuntu-latest
    steps:
      # Checkout code without initializing submodules
      - uses: actions/checkout@v4
        with:
          submodules: false # Defer submodule initialization

      # Restore Git Submodules Cache
      - name: Restore Git Submodules Cache
        uses: actions/cache@v4
        with:
          path: .git/modules
          key: submodules-${{ github.ref_name }}
          restore-keys: |
            submodules-${{ github.ref_name }}
            submodules-

      # Git Submodule Update
      - name: Git Submodule Update
        run: |
          git submodule sync
          git submodule update --init --recursive
          git submodule foreach "git fetch origin main && git reset --hard origin/main"

      # Cache Git Submodules
      - name: Cache Git Submodules
        uses: actions/cache@v4
        with:
          path: .git/modules
          key: submodules-${{ github.ref_name }}

      # Restore Node.js Modules Cache
      - name: Restore Node.js Modules Cache
        uses: actions/cache@v4
        with:
          path: ~/.npm
          key: npm-cache-${{ env.NODE_VERSION }}-${{ github.ref_name }}
          restore-keys: |
            npm-cache-${{ env.NODE_VERSION }}-${{ github.ref_name }}
            npm-cache-${{ env.NODE_VERSION }}-
            npm-cache-

      # Use Node.js
      - name: Use Node.js ${{ env.NODE_VERSION }}
        uses: actions/setup-node@v4
        with:
          node-version: ${{ env.NODE_VERSION }}

      # Install dependencies
      - name: Install dependencies
        run: npm ci

      # Save Node.js Modules Cache
      - name: Save Node.js Modules Cache
        uses: actions/cache@v4
        with:
          path: ~/.npm
          key: npm-cache-${{ env.NODE_VERSION }}-${{ github.ref_name }}

      - name: Build
        run: npm run build-github

      - name: Deploy
        uses: peaceiris/actions-gh-pages@v4
        with:
          publish_dir: dist
          github_token: ${{ secrets.GITHUB_TOKEN }}
          force_orphan: true
          publish_branch: gh-pages
{% endraw %}
```
{% enddetails %}

### Ajout de fonctionnalités

Ce rework apporte un grand nombre de nouvelles fonctionnalités qui vont révolutionner l'expérience utilisateur du site Do-It.

#### Plugins front-end

Pour améliorer l'expérience utilisateur et réduire le nombre d'images uploadées, j'ai ajouté / rendu fonctionnels de nombreux plugins javascript:

##### PrismJS

PrismJS est un plugin javascript qui permet de styliser les blocs de code source dans les fichiers markdown.\
Il est très utile pour mettre en avant les blocs de code et les rendre plus lisibles.

J'ai ajouté en particulier les extensions PrismJS suivantes:
- `line-numbers` : pour afficher les numéros de ligne
- `copy-to-clipboard` : pour afficher un bouton de copie du code
- `show-language` : pour afficher le langage du code
- `toolbar` : pour afficher la barre d'outils (bouton de copie, langage)
- `normalize-whitespace` : pour effacer les espaces blancs inutiles

##### MermaidJS

MermaidJS est un plugin javascript qui permet de générer des diagrammes à partir de code source.\
Il est très utile pour générer des diagrammes de flux, des diagrammes de séquence, des diagrammes de Gantt, des graphique,...

##### MathJax

MathJax est un plugin javascript qui permet de générer des formules mathématiques à partir de code source en latex.\
Il est très utile pour générer des formules mathématiques complexes et les afficher dans les fichiers markdown.

#### Fonctionnalités eleventy

##### Variables

J'ai ajouté des variables eleventy pour stocker des choses importantes et récurrentes pour le site.
On peut retrouver les variables dans les fichiers [{{ site.source }}/tree/main/_data/]({{ site.source }}/tree/main/_data/).\
Ces variables sont explicitées dans les guides de contribution.

##### Shortcodes

J'ai ajouté des shortcodes eleventy pour générer des éléments HTML récurrents dans les fichiers markdown.
On peut retrouver les shortcodes dans les fichiers [{{ site.source }}/tree/main/scripts/eleventy/markdown/shortcodes/]({{ site.source }}/tree/main/scripts/eleventy/markdown/shortcodes/).\
Ces shortcodes sont explicités dans les guides de contribution.

##### markdown-it-anchor

markdown-it-anchor est un plugin eleventy qui permet de générer des ancres automatiquement pour les titres des fichiers markdown.\
Cela permet de naviguer plus facilement dans les fichiers markdown et de partager des liens vers des sections spécifiques.

##### markdown-it-toc-done-right

markdown-it-toc-done-right est un plugin eleventy qui permet de générer une table des matières automatiquement pour les fichiers markdown.\
Cela permet de naviguer plus facilement dans les fichiers markdown et de voir la structure du document.

#### Post build

##### html-minifier-terser

html-minifier-terser est un plugin javascript qui permet de minifier le code HTML.\
Cela permet de réduire la taille des fichiers HTML et d'accélérer le chargement des pages, en plus de réduire la consommation de bande passante.

##### posthtml-url

posthtml-url est un plugin eleventy qui permet de réécrire les URLs des médias dans les fichiers HTML.\
Cela permet de pointer vers les médias stockés sur GitHub et de réduire la taille du build.

### Migration & GitOps

Afin de ne plus être dépendant de GitHub Pages, il a été décidé d'utiliser nos propres serveurs pour héberger et exposer le site Do-It.

L'idée est d'utiliser un serveur Nginx configuré pour servir les fichiers statiques du site Do-It.\
Il faut aussi pouvoir **mettre à jour le site automatiquement** à chaque push sur la branche `gh-pages`.

#### Configuration de la machine

Sur notre fier serveur aioli, j'ai créé une machine virtuelle [alpine](https://alpinelinux.org/) vierge que j'ai entièrement configurée pour servir le site Do-It de manière optimale.

L'intérêt d'Alpine est que c'est un OS ultra léger, qui ne contient que le strict nécessaire pour fonctionner. La surface d'attaque est donc très réduite. La machine virtuelle n'a besoin que de 1Go d'espace disque et 512Mo de RAM pour fonctionner.

{% details "Configuration de la machine" %}
Ce script permet d'exécuter d'une traite toutes les configurations pour la machine virtuelle (en supposant que le `setup-alpine` est déjà **fait**).
```sh
#!/bin/sh
apk update && \
apk upgrade && \
apk add --no-cache nginx git python3 openrc && \
rm -rf /var/cache/apk/* && \
echo "Creating the do-it user and directory" && \
addgroup -S do-it && \
adduser -S -D -h /home/do-it -G do-it do-it && \
mkdir -p /home/do-it/.do-it/jobs && \
echo "Creating the nginx configuration file in /etc/nginx/http.d/do-it.conf" && \
rm -f /etc/nginx/http.d/default.conf && \
cat <<'EOF' > /etc/nginx/http.d/do-it.conf
server {
    # Listen on IPv4 and IPv6
    listen 80;
    listen [::]:80;

    # Serve static files
    root /home/do-it/.do-it/do-it;
    index index.html;

    # Handle requests
    location / {
        # If the request is a POST, forward it to the python update server
        if ($request_method = POST) {
            proxy_pass http://localhost:3001;
            break;
        }

        # Serve static files for other requests
        try_files $uri $uri/ =404;
    }

    # Custom error page for 404 errors
    error_page 404 /404.html;
    location = /404.html {
        internal;
    }
}
EOF

echo "Creating the synchronizer script in /home/do-it/.do-it/jobs/synchronizer.sh" && \
cat <<'EOF' > /home/do-it/.do-it/jobs/synchronizer.sh
#!/bin/sh

DO_IT_PATH="${HOME}/.do-it/do-it"
REMOTE_BRANCH="gh-pages"
LOG_DIRECTORY="${HOME}/.do-it/logs"
LOG_FILE="${LOG_DIRECTORY}/synchronizer.log"

mkdir -p ${LOG_DIRECTORY}

# Function to prepend a formatted timestamp
log_with_timestamp() {
  while IFS= read -r line; do
    echo "$(date '+%Y/%m/%d %Hh%M:%S') $line"
  done
}

cd ${DO_IT_PATH} && \
GIT_ORIGIN_URL="$(git remote get-url origin)" && \
git fetch origin ${REMOTE_BRANCH} 2>&1 | log_with_timestamp | tee -a ${LOG_FILE} && \
git reset --hard origin/${REMOTE_BRANCH} 2>&1 | log_with_timestamp | tee -a ${LOG_FILE} && \
echo "Synchronized with the remote origin ${GIT_ORIGIN_URL} ${REMOTE_BRANCH} branch" 2>&1 | log_with_timestamp | tee -a ${LOG_FILE}
EOF

echo "Creating the server script in /home/do-it/.do-it/jobs/server.py" && \
cat <<'EOF' > /home/do-it/.do-it/jobs/server.py
# coding: utf-8
"""
Create a simple HTTP server that listens on a specified port.
The server receives POST requests, validates the token, and triggers a script.
Logs are written to a specified log file.
"""

from os import path, makedirs
import argparse
import logging
from http.server import HTTPServer, BaseHTTPRequestHandler
from subprocess import Popen, PIPE
from json import loads, JSONDecodeError
import hashlib
import hmac

class HTTPError(Exception):
    def __init__(self, status_code: int, detail: str):
        self.status_code = status_code
        self.detail = detail
        super().__init__(self.detail)

class WebhookHandler(BaseHTTPRequestHandler):
    def verify_signature(self, secret_token):
        """
        Verify the request payload's signature using the secret token.
        """
        signature_header = self.headers.get('X-Hub-Signature-256')
        payload_length = int(self.headers.get('Content-Length', 0))
        payload_body = self.rfile.read(payload_length).decode('utf-8')

        if secret_token:
            if not signature_header:
                raise HTTPError(401, "Missing signature header")

            hash_object = hmac.new(secret_token.encode('utf-8'), msg=payload_body.encode('utf-8'), digestmod=hashlib.sha256)
            expected_signature = "sha256=" + hash_object.hexdigest()
            if not hmac.compare_digest(expected_signature, signature_header):
                raise HTTPError(403, "Invalid request signature")

        try:
            parsed_body = loads(payload_body)
        except JSONDecodeError:
            raise HTTPError(400, "Invalid JSON payload")

        return parsed_body

    def do_POST(self):
        """
        Handle POST requests, validate payload, and trigger script execution.
        """
        try:
            # Verify the request signature and extract JSON payload
            request_body = self.verify_signature(self.server.secret_token)

            # Validate repository and branch
            repo_full_name = request_body['repository'].get('full_name')
            ref = request_body['ref']
            if repo_full_name != f"{self.server.github_repo_owner}/{self.server.github_repo}":
                raise HTTPError(400, f"Repository mismatch. Expected {self.server.github_repo_owner}/{self.server.github}")
            if ref != f"refs/heads/{self.server.github_branch}":
                raise HTTPError(400, f"Branch mismatch. Expected {self.server.github_branch}")

            # Run the update script if provided
            if self.server.update_script:
                self.run_script(self.server.update_script)

            self.send_response(200)
            self.end_headers()
            self.wfile.write(b"Webhook processed successfully.")
        except HTTPError as e:
            self.send_response(e.status_code)
            self.end_headers()
            self.wfile.write(e.detail.encode('utf-8'))
            logging.error(f"HTTPError: {e.detail}")
        except Exception as e:
            self.send_response(500)
            self.end_headers()
            self.wfile.write(f"Error: {e}".encode('utf-8'))
            logging.error(f"Unexpected error: {e}")

    @staticmethod
    def run_script(script_path):
        """
        Execute the update script.
        """
        logging.info(f"Executing script: {script_path}")
        process = Popen([script_path], stdout=PIPE, stderr=PIPE)
        stdout, stderr = process.communicate()
        if stderr:
            logging.error(f"Script error: {stderr.decode('utf-8')}")
            raise Exception(f"Script error: {stderr.decode('utf-8')}")
        logging.info(f"Script output: {stdout.decode('utf-8')}")
        logging.info("Script executed successfully")

    def log_message(self, format, *args):
        """
        Log an arbitrary message to the logger.
        """
        logging.info("%s - - [%s] %s\n" %
                     (self.client_address[0],
                      self.log_date_time_string(),
                      format % args))

def run_server(host, port, secret_token, update_script, github_repo_owner, github_repo, github_branch):
    """
    Start the web server on the specified host and port.
    """
    server = HTTPServer((host, port), WebhookHandler)
    server.secret_token = secret_token
    server.update_script = update_script
    server.github_repo_owner = github_repo_owner
    server.github_repo = github_repo
    server.github_branch = github_branch

    logging.info(f"Starting server on {host}:{port}")
    try:
        server.serve_forever()
    except KeyboardInterrupt:
        server.shutdown()
        logging.info("Server stopped.")

def main():
    parser = argparse.ArgumentParser(description="Simple HTTP server to handle GitHub webhooks.")
    parser.add_argument('--host', default='localhost', help='Hostname to bind the server to (default: ::)')
    parser.add_argument('--port', type=int, default=3001, help='Port to listen on (default: 3001)')
    parser.add_argument('--secret-token', help='Secret token to validate incoming requests')
    parser.add_argument('--update-script', required=True, help='Path to the script to execute upon valid webhook')
    parser.add_argument('--github-repo-owner', required=True, help='GitHub repository owner')
    parser.add_argument('--github-repo', required=True, help='GitHub repository name')
    parser.add_argument('--github-branch', required=True, help='GitHub branch to monitor for webhooks')
    parser.add_argument('--log-file', required=True, help='Path to the log file (default: server.log)')

    args = parser.parse_args()

    # Create log directory if it does not exist
    log_dir = path.dirname(args.log_file)
    makedirs(log_dir, exist_ok=True)

    # Configure logging
    logging.basicConfig(
        filename=args.log_file,
        level=logging.INFO,
        format='%(asctime)s - %(levelname)s - %(message)s'
    )

    run_server(
        host=args.host,
        port=args.port,
        secret_token=args.secret_token,
        update_script=args.update_script,
        github_repo_owner=args.github_repo_owner,
        github_repo=args.github_repo,
        github_branch=args.github_branch
    )

if __name__ == "__main__":
    main()
EOF

echo "Creating the init script in /etc/init.d/do-it-webserver" && \
cat <<'EOF' > /etc/init.d/do-it-webserver
#!/sbin/openrc-run
name="do-it-webserver"
description="Do-It Git Update Signals Python Web Server"

command="/usr/local/bin/do-it-webserver.sh"
command_user="do-it"

pidfile="/var/run/${RC_SVCNAME}.pid"
logfile="/var/log/${RC_SVCNAME}.log"

depend() {
    need net
}

start_pre() {
    checkpath --file --owner $command_user:$command_user --mode 0644 $logfile
}

supervisor="supervise-daemon"
output_log="${logfile}"
error_log="${logfile}"
command_background="yes"
EOF

echo "Creating the web server service script in /usr/local/bin/do-it-webserver.sh" && \
cat <<'EOF' > /usr/local/bin/do-it-webserver.sh
#!/bin/sh
python3 /home/do-it/.do-it/jobs/server.py --update-script /home/do-it/.do-it/jobs/synchronizer.sh --github-repo-owner do-it-ecm --github-repo do-it --github-branch gh-pages --secret-token EXAMPLETOKEN --log-file /home/do-it/.do-it/logs/server.log
EOF

echo "Cloning the do-it repository" && \
git clone --branch gh-pages --single-branch https://github.com/do-it-ecm/do-it.git /home/do-it/.do-it/do-it && \
echo "Setting permissions" && \
chown -R do-it:do-it /home/do-it && \
chmod -R 755 /home/do-it && \
rc-update add nginx default && \
chmod +x /usr/local/bin/do-it-webserver.sh && \
chmod +x /etc/init.d/do-it-webserver && \
rc-update add do-it-webserver default && \
sleep 5 && \
echo "Starting the services" && \
rc-service nginx start
rc-service do-it-webserver start
```
{% enddetails %}

Ce script met en place un serveur Nginx pour **servir** les fichiers statiques du site Do-It et un serveur Python pour écouter les webhooks GitHub et **mettre à jour** le site automatiquement.\
Ces deux services redémarrent automatiquement en cas de crash.\
Il faut simplement penser à **remplacer `EXAMPLETOKEN` par le token GitHub** dans le script.
