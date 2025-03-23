---
layout: layout/mon.njk

title: "Attaques DDoS en Cybersécurité"
authors:
  - "Sofiane Ouadda"
date: 2024-12-21
temps: 3
tags:
  - "Cybersécurité"
  - "Réseau"
  - "Sécurité Informatique"
  - "DDoS"
  - "Protection"

description: "Ce document explore les attaques DDoS, leurs mécanismes, ainsi que les méthodes de prévention et de protection. Il aborde également les bonnes pratiques en matière de défense et de surveillance pour sécuriser un système d'information."

---

{% prerequis %}

- Connaissances de base en réseau (modèle TCP/IP, protocoles, etc.)
- Notions de sécurité informatique (firewalls, VPN, etc.)

{% endprerequis %}

{% lien %}

- [Cloudflare - Qu’est-ce qu’une attaque DDoS ?](https://www.cloudflare.com/fr-fr/learning/ddos/what-is-a-ddos-attack/)
- [OWASP - Denial of Service](https://owasp.org/www-community/attacks/Denial_of_Service)
- [Krebs on Security - DDoS Resources](https://krebsonsecurity.com/tag/ddos/)
- [YouTube - DDoS Explanation](https://www.youtube.com/watch?v=ilhGh9CEIwM&pp=ygUVZGRvcyBhdHRhY2sgZXhwbGFpbmVk)
- **CERT-FR** – Bulletins de sécurité et alertes sur les attaques DDoS (disponibles sur [cert.ssi.gouv.fr](https://www.cert.ssi.gouv.fr/))

{% endlien %}

---

## Objectifs
1. Comprendre le fonctionnement d’une attaque DDoS (principe, vecteurs, cibles).
2. Identifier les différentes variantes d’attaques DDoS (UDP flood, SYN flood, amplification, etc.).
3. Découvrir les outils et méthodologies pour détecter et atténuer les attaques DDoS.
4. Présenter des bonnes pratiques pour protéger une organisation contre les DDoS.
5. Analyser des cas réels d’attaques DDoS et comprendre leurs impacts techniques, financiers et médiatiques.

---

## 1. Introduction

Une attaque par DoS, (Denial of Service) vise à rendre un service (site web, serveur de messagerie, plateforme de jeu en ligne, etc.) **indisponible** pour ses utilisateurs légitimes. Lorsqu’une attaque implique **plusieurs** machines coordonnées, on parle alors d’**attaque DDoS** (Distributed Denial of Service).

### 1.1 Pourquoi s’intéresser aux DDoS ?

- **Impacts financiers** : Un site d’e-commerce attaqué perd des ventes pendant toute la durée de l’indisponibilité.
- **Risque réputationnel** : Les clients perdent confiance si un service est fréquemment hors-ligne.
- **Amplification des menaces** : Avec la multiplication des objets connectés (IoT), il est devenu plus simple de monter de vastes réseaux (botnets) capables de lancer des attaques massives.

### 1.2 Qui peut être visé ?

- **Entreprises** (sites marchands, plateformes SaaS).
- **Organisations gouvernementales** (sites d’administrations, portails de services publics).
- **Fournisseurs de services réseau** (hébergeurs, FAI).
- **Particuliers** ayant mis en place un service en ligne (serveur de jeu, blog populaire, etc.).

Bien qu’un particulier soit moins exposé qu’une grande entreprise, il est tout à fait possible qu’une personne subisse une attaque DDoS si elle est ciblée (ex. harcèlement en ligne, rivalités dans le domaine du gaming, etc.).

---

## 2. Mécanismes généraux d’une attaque DDoS

### 2.1 Notion de botnet

Pour comprendre le DDoS, il faut imaginer un **botnet** : un ensemble d’ordinateurs (ou d’objets connectés) contaminés par un logiciel malveillant. Ces machines sont appelées des **“zombies”** parce qu’elles obéissent **à distance** à l’attaquant, sans que le propriétaire légitime s’en rende forcément compte.

Un **botmaster** (celui qui contrôle le réseau) utilise un **serveur de Command & Control (C&C)** pour donner des ordres aux zombies : “Envoie des milliers de paquets TCP/UDP par seconde à telle adresse IP, sur tel port”.

### 2.2 L’effet de masse

Contrairement à une attaque DoS menée depuis un seul ordinateur, le DDoS s’appuie sur **des centaines, des milliers voire des millions** de machines différentes. Le volume de trafic généré peut être colossal, saturant :

- **La bande passante** de la cible (envois massifs de données).
- Les **ressources du serveur** (mémoire, processeur, nombre de connexions simultanées).

Même si la cible dispose d’un bon débit, une attaque DDoS bien coordonnée peut la rendre inaccessible en quelques minutes.

### 2.3 Principaux objectifs

- **Surcharger** la cible pour qu’elle ne réponde plus aux utilisateurs légitimes.
- **Noyer** la cible sous un trafic qui dépasse sa capacité de traitement.
- **Perturber les services** critiques (serveurs DNS, serveurs web, bases de données).

---

## 3. Types d’attaques DDoS

Les attaques DDoS se distinguent par leur **mode de fonctionnement** et **le protocole** exploité.

### 3.1 Attaques volumétriques

#### 3.1.1 UDP Flood
- Exploite le protocole **UDP (User Datagram Protocol)** qui ne nécessite pas d’établissement de connexion préalable.
- L’attaquant inonde la cible avec des paquets UDP sur divers ports, la forçant à vérifier constamment si un service est à l’écoute.
- Peut conduire à une **surcharge de la bande passante** ou des ressources du serveur.

#### 3.1.2 ICMP Flood (Ping Flood)
- Utilise des **paquets ICMP (Internet Control Message Protocol)**, le protocole de base pour les pings.
- En envoyant une avalanche de requêtes ping, on submerge la capacité de la machine à y répondre.
- Parfois couplé à un “smurf attack” (vieille forme d’attaque consistant à envoyer des requêtes ICMP à un réseau entier en usurpant l’adresse IP de la cible).

#### 3.1.3 DNS Amplification
- Tire parti de **serveurs DNS mal configurés** pour amplifier le trafic.
- L’attaquant envoie une petite requête DNS falsifiée (usurpant l’IP de la victime) et reçoit en retour une **grosse** réponse DNS envoyée à la cible.
- Permet d’atteindre des débits énormes (facteur d’amplification jusqu’à x50 ou x100 selon les cas).

### 3.2 Attaques protocolaires

#### 3.2.1 SYN Flood
- Exploite le mécanisme de **TCP** (la fameuse “poignée de main” en trois temps : SYN, SYN-ACK, ACK).
- L’attaquant envoie un grand nombre de **requêtes SYN** mais **n’achève jamais** la connexion (pas de ACK final).
- Résultat : les ressources du serveur (tables de connexion) se remplissent rapidement, empêchant toute connexion légitime.

#### 3.2.2 ACK/RST Flood
- Envoi massif de **paquets ACK** ou **RST** pour saturer la pile TCP de la victime.
- Peut empêcher la finalisation ou la rupture propre de connexions légitimes.

### 3.3 Attaques applicatives (couche 7)

#### 3.3.1 HTTP GET/POST Flood
- “Bombarder” un serveur web de **requêtes HTTP** (parfois sur des pages dynamiques et coûteuses à générer).
- Peut faire exploser la charge CPU et la base de données associée.
- Souvent difficile à distinguer du trafic légitime, car ce sont de “vraies” requêtes HTTP.

#### 3.3.2 Slowloris
- Envoi de requêtes HTTP **très fragmentées**, maintenant la session ouverte le plus longtemps possible.
- Le serveur conserve les connexions partiellement ouvertes, gaspillant ses ressources (threads).
- Redoutable contre certains serveurs mal configurés.

#### 3.3.3 XML-RPC ou SOAP
- Attaques spécifiques visant des **services web** (API REST, SOAP, XML-RPC).
- En envoyant un grand nombre de requêtes complexes, on épuise la charge d’un serveur applicatif.

---

## 4. Détection et atténuation d’une attaque DDoS

### 4.1 Comment détecter une attaque ?

1. **Monitoring réseau** : si la consommation de bande passante grimpe soudainement, c’est un indice.
2. **Surveillance des logs** : multiplication anormale de requêtes similaires, venant d’adresses IP différentes.
3. **Outils d’alerting** : Zabbix, Grafana, Nagios, etc. qui déclenchent des alertes si la latence ou le taux de CPU s’envolent.
4. **IDS/IPS** (Intrusion Detection/Prevention Systems) : peuvent repérer des schémas d’attaque connus ou un flux inhabituel.
5. **SIEM** (Security Information and Event Management) : recoupe les événements de plusieurs sources pour identifier des attaques DDoS multi-vectorielles.

### 4.2 Techniques de défense

1. **Scrubbing centers** : rediriger le trafic vers des centres de “nettoyage” où on analyse et filtre les paquets.
2. **CDN et services DDoS** : Cloudflare, Akamai, Imperva, AWS Shield. Ils “absorbent” le flux et ne laissent passer que les requêtes légitimes.
3. **Rate Limiting** : limitation du nombre de requêtes par IP ou par session sur une période donnée.
4. **Blackhole / Sinkhole** : rediriger le trafic malveillant vers une sorte de “poubelle numérique” pour protéger l’infrastructure critique.
5. **SYN Cookies** : solution pour éviter de stocker l’état de la connexion tant que la poignée de main n’est pas finalisée.
6. **Paramétrages firewall avancés** : bloquer certaines plages d’IP, filtrer des ports inhabituels, etc.

---

## 5. Le marché du DDoS : une économie illégale en pleine expansion

Au-delà de l’aspect purement technique, il existe désormais un **véritable marché du DDoS**, alimenté par des plateformes dites **“DDoS-for-hire”** (ou **“booter services”**). Ces services, accessibles via de simples sites web ou des forums clandestins, proposent à quiconque de louer la puissance d’un **botnet** pour lancer une attaque DDoS. Souvent, un paiement en cryptomonnaie suffit pour initier quelques minutes ou plusieurs heures d’agression contre une cible.

### Facteurs clés de cette expansion
- **Accessibilité** : Nul besoin de maîtriser la cybersécurité ; une interface web simplifiée et un système de paiement (cryptomonnaies, cartes prépayées) rendent ces services à la portée de tous.
- **Croissance du botnet IoT** : La prolifération d’objets connectés (caméras IP, routeurs, etc.) mal protégés fournit une vaste ressource de machines zombies à faible coût.
- **Tarification “à la carte”** : Les plate-formes proposent souvent des formules d’abonnement ou de packs d’attaques, modulables selon la durée, l’intensité ou le protocole choisi (UDP flood, HTTP flood, etc.).
- **Failles législatives** : Les poursuites sont compliquées lorsqu’un service opère depuis un pays où la législation est laxiste ou la collaboration judiciaire internationale inexistante.

### Exemples de services et tarifs

- **WebStresser** : jadis au cœur d’une opération de police internationale. Proposait des plans mensuels de 15$ à 50$, permettant de lancer des attaques sur plusieurs vecteurs (UDP, TCP, HTTP).
- **Quantum Booter** : interface utilisateur très simple, forfaits démarrant à **15$ par mois**. Possibilité d’augmenter la durée ou la puissance de l’attaque avec des formules “premium”.
- **IPStresser / StressThem** : régulièrement cités dans des enquêtes sur le cybercrime. Les tarifs varient de **20$** (attaques brèves) à plus de **100$** pour des sessions prolongées ou illimitées.

### Tarification et formules courantes
- **Abonnements mensuels** : De **15$ à 80$** pour un nombre limité ou illimité de frappes quotidiennes.
- **Plans “Premium”** : Atteignant plusieurs centaines de dollars, permettant des attaques plus longues (parfois jusqu’à 24 h) ou en simultané sur plusieurs cibles.
- **Paiements anonymes** : Le plus souvent acceptés en cryptomonnaie (Bitcoin, Monero) pour dissimuler l’identité de l’acheteur.

### Conséquences et banalisation
- Des **attaques massives** peuvent désormais être déclenchées par **n’importe qui**, pour un coût dérisoire.
- Les victimes sont diverses : entreprises, particuliers, services gouvernementaux, hébergeurs, etc.
- La difficulté pour les forces de l’ordre réside dans le **caractère décentralisé** de ces services, qui changent régulièrement de nom et de domaine pour éviter les fermetures.

 La facilité d’accès et la **forte rentabilité** pour les vendeurs font du marché DDoS une véritable économie souterraine. Pour contrer ce phénomène, les acteurs de la cybersécurité insistent sur le besoin de **mieux sécuriser les terminaux** (objets connectés, serveurs vulnérables), de **renforcer la coopération internationale** et de **sensibiliser** les utilisateurs, afin de limiter les opportunités offertes aux groupes criminels.


## 6. Bonnes pratiques de protection

1. **Dimensionner l’infrastructure** : avoir une marge de bande passante et de puissance serveurs au-dessus de la moyenne du trafic habituel.
2. **Choisir des hébergeurs offrant des options anti-DDoS** : Beaucoup de fournisseurs proposent maintenant des pare-feu dédiés et des solutions de mitigation.
3. **Séparer les services critiques** (base de données, service web, etc.) pour éviter qu’une seule attaque n’affecte toutes les briques.
4. **Mises à jour régulières** : systèmes d’exploitation, firmwares, logiciels applicatifs (corriger les failles et profiter des optimisations).
5. **Plan de réponse et de continuité** : décrire clairement comment réagir en cas d’attaque (personnes à contacter, mesures d’urgence, basculement possible vers un autre site).
6. **Test de charge** : simuler un pic de trafic ou une mini-attaque DDoS pour vérifier la réactivité de l’infrastructure.

---

## 7. Études de cas réels

Dans l’histoire d’Internet, plusieurs **attaques DDoS retentissantes** ont mis en lumière la vulnérabilité de grands acteurs. Voici trois études de cas marquantes.

### 7.1 GitHub (2018)

**Contexte**
- GitHub que vous devez tous bien connaitre en cette fin d'année, sert au développement collaboratif en hebergeant du code.
- En février 2018, GitHub a été victime d’une des attaques DDoS les plus importantes jamais enregistrées à l’époque.

**Caractéristiques de l’attaque**
- **Pic de trafic** : Environ **1,35 térabit par seconde (Tbps)**, un record pour l’époque.
- Le vecteur principal était une **attaque d’amplification Memcached**. Memcached est un système de cache d’objets en mémoire, normalement utilisé pour accélérer les sites web. S’il est exposé sur Internet sans protection, un attaquant peut envoyer de petites requêtes UDP usurpant l’IP de la victime. Les réponses, beaucoup plus volumineuses, sont alors retournées à la cible (GitHub), saturant sa bande passante.
- GitHub a rapidement remarqué l’attaque grâce à son système de détection.

**Réponse et mitigation**
- **Redirection du trafic** vers un service de “scrubbing” : GitHub a basculé son trafic vers une infrastructure spécialisée capable de filtrer les paquets illégitimes.
- **Durée** : L’attaque n’a duré que quelques minutes à son intensité maximale, mais a suffi à prouver la puissance de l’amplification Memcached.
- **Enseignements** : L’importance de **configurer correctement** les services Memcached (pas de port ouvert sur Internet) et de surveiller en temps réel son trafic.

### 7.2 Dyn (2016)

**Contexte**
- Dyn est un fournisseur de services DNS (Domain Name System). Les DNS sont la “carte” qui permet de faire la correspondance entre les noms de domaine (ex. google.com) et les adresses IP.
- En octobre 2016, une attaque DDoS massive a visé Dyn, entraînant la paralysie de nombreux sites majeurs (Twitter, Spotify, Reddit, Netflix, Amazon, etc.).

**Caractéristiques de l’attaque**
- L’attaque a été perpétrée par le **botnet Mirai**. Mirai ciblait les objets connectés mal sécurisés (caméras de surveillance, routeurs domestiques).
- Des millions d’appareils IoT infectés ont ainsi pu envoyer un volume gigantesque de trafic vers les serveurs DNS de Dyn.
- En saturant les DNS, les sites utilisant Dyn comme prestataire ne pouvaient plus être résolus correctement — les utilisateurs voyaient apparaître des erreurs ou ne pouvaient plus accéder à ces services.

**Réponse et mitigation**
- Dyn a rapidement mobilisé ses équipes et son infrastructure, tentant de filtrer et rediriger le trafic malveillant.
- Malgré tout, des **pannes** se sont étalées sur plusieurs heures, affectant différents services par intermittence.
- **Leçon principale** : la **vulnérabilité de l’écosystème IoT** et la dépendance critique à des points centraux (comme un DNS) qui, s’ils tombent, impactent de nombreux sites.
- Depuis, de nombreuses entreprises ont investi dans des DNS redondants et mis en place des politiques de protection des appareils connectés (mises à jour, mots de passe forts, etc.).

### 7.3 Spamhaus (2013)

**Contexte**
- Spamhaus est une organisation à but non lucratif qui maintient des listes noires d’adresses IP connues pour diffuser du spam. Les fournisseurs de messagerie et d’autres services utilisent ces listes pour bloquer les expéditeurs indésirables.
- En mars 2013, Spamhaus a été ciblée par une attaque d’ampleur.

**Caractéristiques de l’attaque**
- Le groupe Cyberbunker, lié à un hébergeur controversé, aurait orchestré l’attaque.
- **Méthode** : **DNS Amplification** et **autres techniques volumétriques**.
- **Volume** : Environ 300 Gbps à l’époque, ce qui était déjà extrêmement élevé.

**Réponse et mitigation**
- Spamhaus a collaboré avec Cloudflare pour rediriger et filtrer le trafic.
- Les FAI européens ont dû adapter leurs infrastructures pour éviter la congestion de certains “nœuds” Internet, car le volume de données risquait de ralentir la navigation de millions d’utilisateurs.
- L’incident a montré la nécessité de **configurer correctement les serveurs DNS** (limiter les réponses récursives, mettre en place des contrôles d’accès) afin d’éviter d’être une source d’amplification.

---

## 8. Conclusion

Les attaques DDoS restent l’une des menaces les plus prégnantes dans le paysage de la **cybersécurité**. Elles s’appuient sur la **force de frappe collective** (botnets), l’utilisation de **failles de configuration** (DNS, Memcached) et la difficulté de distinguer un trafic légitime d’un trafic malveillant (cas des attaques couche 7).

**Points-clés** :
- Surveiller son trafic et disposer de **systèmes de détection** performants.
- Mettre en œuvre des **services de protection DDoS** (CDN, scrubbing centers) pour absorber les attaques volumétriques.
- **Sécuriser** ses infrastructures (mise à jour, firewall, limites de connexions).
- **Anticiper** (plans de continuité, redondance DNS) pour éviter une panne totale en cas d’attaque.

À mesure que le nombre d’appareils connectés augmente, les possibilités de constituer des botnets gigantesques s’accroissent. Déployer les **bonnes pratiques** décrites dans ce document est donc essentiel pour qu’un service puisse rester disponible même sous forte pression.

---

## Horodateur

| Date   | Heures passées | Indications                                                                                                  |
|--------|----------------|--------------------------------------------------------------------------------------------------------------|
| 12/12  | 1H30           | Lecture préliminaire des ressources Cloudflare et OWASP, notes sur le fonctionnement général des attaques DDoS |
| 14/12  | 2H30             | Étude approfondie des différents vecteurs d’attaque (SYN Flood, UDP Flood, DNS Amplification) |
| 16/12  | 2H          | Recherche sur les techniques de mitigation (Firewalls, IDS/IPS, services CDN, etc.), comparaison des solutions |
| 18/12  | 2H30             | Comprendre comment on pouvait détecter et atténuer les attaques DDoS et études des « Bonnes pratiques de protection »     |
| 20/12  | 2H           | Analyse de cas concrets                    |



---