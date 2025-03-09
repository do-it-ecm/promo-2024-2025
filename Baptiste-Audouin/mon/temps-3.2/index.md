---
layout: layout/mon.njk

title: "Analyse de données météorologiques avec R"
authors:
  - Baptiste Audouin

date: 2025-03-09
temps: 3
tags:

résumé: "Ce MON traite de la découverte du langage R à travers l'analyse de données météorologiques."
---

{% prerequis %}

Aucun prérequis.

{% endprerequis %}
{% lien %}

- [Kaggle - Weather Data](https://www.kaggle.com/datasets/prasad22/weather-data/data)
- [Mon Github](https://github.com/baptiste7905/MON3.2)

{% endlien %}


## Introduction

À travers ce MON, j'ai choisi de travailler sur un jeu de données météorologiques de Los Angeles. Ce dataset contient des informations sur la température, l'humidité, les précipitations et la vitesse du vent. Mon objectif était de manipuler, visualiser et prédire ces données pour mieux comprendre les tendances météorologiques afin d'approfondir mes connaissances en R.

## 1. Le dataset (source et description)

Le dataset utilisé dans ce projet provient de Kaggle et contient des données météorologiques quotidiennes pour la ville de Los Angeles entre janvier et mai 2024. Il comprend les colonnes suivantes :

- **Date_Time** : La date et l'heure de l'enregistrement.
- **Temperature_C** : La température en degrés Celsius.
- **Humidity_pct** : L'humidité pourcentage.
- **Precipitation_mm** : Les précipitations en millimètres.
- **Wind_Speed_kmh** : La vitesse du vent en kilomètres par heure.

Ce dataset m'a permis d'explorer les variations météorologiques et de découvrir les outils de manipulation et de visualisation de R.

## 2. Nettoyage des données

### Encodage et format de date

Les données ont été chargées à partir d'un fichier CSV. La colonne Date_Time était initialement au format texte (dd/mm/YYYY HH:MM). J'ai utilisé la fonction as.POSIXct() pour la convertir en format datetime :

````bash
df$Date_Time <- as.POSIXct(df$Date_Time, format = "%d/%m/%Y")
````

Ensuite, j'ai extrait la date seule avec as.Date() pour faciliter l'analyse quotidienne :

```bash
df$Date <- as.Date(df$Date, format = "%d/%m/%Y")
```

### Moyennes par jour

Comme les données contenaient plusieurs enregistrements par jour, j'ai calculé les moyennes quotidiennes pour chaque variable :

```bash
df_daily <- df %>%
  group_by(Date) %>%
  summarise(
    Temperature_C = mean(Temperature_C, na.rm = TRUE),
    Humidity_pct = mean(Humidity_pct, na.rm = TRUE),
    Precipitation_mm = mean(Precipitation_mm, na.rm = TRUE),
    Wind_Speed_kmh = mean(Wind_Speed_kmh, na.rm = TRUE)
  )
```
Ce nouveau dataset (df_daily) a servi de base pour les analyses et visualisations suivantes.

##  3. Visualisation des données

### Courbes d'évolution

J'ai utilisé ggplot2 pour tracer l'évolution de la température et de l'humidité au fil du temps. Par exemple, voici la courbe d'évolution de la température :

![Evolution de la température](./images/evolution_temp.png)

### Histogramme

Pour comprendre la répartition de l'humidité, j'ai créé un histogramme :

![Evolution de l'humidité](./images/evolution_humidite.png)

### Relations entre variables

J'ai exploré la relation entre l'humidité et la température à l'aide d'un graphique de dispersion. La ligne rouge représente la régression linéaire, qui montre une tendance positive :

![Relation humidité/température](./images/relation_humidite_temp.png)

On observe une légère tendance positive indiquée par la droite de régression rouge, ce qui voudrait dire que l'humidité augmente légèrement avec la température. Cependant, la dispersion des points est importante, ce qui indique une corrélation très faible entre ces deux variables.

1. Prédictions

### Modélisation avec Prophet

Pour prédire les températures futures, j'ai utilisé le modèle Prophet de Facebook. Voici les étapes :

1. Préparer les données pour Prophet :

```bash
df_prophet <- data.frame(
  ds = df_daily$Date,
  y = df_daily$Temperature_C
)
```

2. Entraîner le modèle :
   
```bash
model_prophet <- prophet(df_prophet)
future <- make_future_dataframe(model_prophet, periods = 30)
```

3. Faire des prévisions pour les 30 prochains jours :
   
```bash
forecast_prophet <- predict(model_prophet, future)
```

4. Visualisation des prévisions

![Prévisions](./images/prev_temp.png)

## Conclusion

Ce projet m'a permis de porsuivre ma découverte de R et ses principales librairies pour manipuler, visualiser et prédire des données. J'ai exploré les tendances météorologiques à travers des graphiques et des modèles de prévision.

