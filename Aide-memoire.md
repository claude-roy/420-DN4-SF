# Aide-mémoire

---
**NOTE**

Ceci est un aide-mémoire et non un cours ni une liste exhaustive de commandes à connaître pour un examen.

---

## Linux 
### Les incontournables

| Commande |  Courte description |
|---|---|
| man | Manuel |
| pwd | Affiche le répertoire courant |
| ls | Liste les fichiers (-a affichage des fichiers cachés, -l affichage long) |
| cd | Change le répertoire courant |
| cat | Concatène des fichiers vers la sortie |
| less | Affiche et pagine un fichier |
| touch | Crée un fichier ou met à jour ses dates |
| head / tail | Affiche le début ou la fin d'un fichier |
| grep | Recherche un motif dans un fichier |
| locate | Recherche de fichiers à partir d'une base de données |
| find | Recherche de fichiers à partir du système de fichiers |
| mount | Monte un système de fichiers |
| diff | Compare des fichiers entre eux |
| cal | Affiche un calendrier |
| wget / curl | Effectue une requête web |
| echo | Affiche un message |
| sudo | Exécute une commande avec les privilèges administrateur |
| su | Change l'utilisateur courant pour celui voulu (root par défaut) |

### Git

| Commande |  Courte description |
|---|---|
| git init | Initialise un dépôt Git |
| git clone | Clone un dépôt Git distant |
| git add | Ajoute un fichier dans le suivi |
| git status | Affiche l'état du dépôt |
| git commit | Valide les modifications |
| git pull | Récupère les modifications distantes |
| git push | Envoie les modifications locales vers le dépôt distant |

### Les éditeurs de texte

| Commande |  Courte description |
|---|---|
| vi / vim | Éditeur classique présent sur la majorité des systèmes |
| nano | Éditeur de texte simple |

### Informations sur le système

| Commande |  Courte description |
|---|---|
| uname | Affiche les informations sur le système |
| df | Affiche l'usage des systèmes de fichiers |


### Manipulations du système de fichiers

#### Manipulations usuelles

| Commande |  Courte description |
|---|---|
| mkdir dir | Crée un répertoire |
| cp | Copie de fichiers / répertoires |
| mv | Déplacement de fichiers / répertoires |
| rm | Supprime un fichier / répertoire |
| ln | Crée un lien vers un fichier |

#### Droits sur les fichiers

| Commande |  Courte description |
|---|---|
| chmod | Modifie les accès à un fichier pour l'utilisateur, le groupe et les autres |
| chown | Modifie le propriétaire d'un fichier |
| chgrp | Modifie le groupe d'un fichier |

### Gestion des processus

| Commande |  Courte description |
|---|---|
| ps | Affiche les processus |
| top | Affiche les processus en temps réel |
| kill | Arrête un processus |

### Gestion du noyau et des modules

| Commande |  Courte description |
|---|---|
| lsmod | Affiche l'état des modules dans le noyau Linux |
| modprobe | Ajoute ou retire des modules du noyau Linux |
| modinfo | Affiche des informations sur un module du noyau Linux |



### Commandes réseau

| Commande |  Courte description |
|---|---|
| ip addr show / ip a | Affiche les adresses IP |
| ip addr show dev enp0s3 | Affiche l'adresse IP de l'interface enp0s3 |
| ip link show | Affiche les interfaces réseau |
| sudo ip link set enp0s3 up/down | Active / désactive une interface réseau |
| ip route | Affiche la table de routage |
| ping | Effectue une suite de requêtes ICMP |
| nslookup | Interroge le serveur DNS |
| sudo nft list ruleset | Affiche les règles du coupe-feu |
| traceroute | Affiche les nœuds traversés vers une destination |

## Docker
### Installation
Installer Docker sous Linux :  

```bash
curl -sSL https://get.docker.com/ | sh
```

**Attention** : cette commande télécharge et exécute un script distant sans vérification préalable. Il est préférable de consulter le script avant de l'exécuter ou d'utiliser l'installation par le dépôt APT officiel de Docker.

### Conteneur

```bash
docker container run -d --publish 8080:80 --name webhost nginx
docker container top webhost
docker container inspect webhost
docker container stats webhost

# Ouvre un shell dans un nouveau conteneur
docker container run -it --name proxy nginx bash
docker container run -it alpine sh
docker container run -it --name ubuntu ubuntu bash
# Relance un conteneur avec un shell interactif
docker container start -ai ubuntu
# Ouvre un shell dans un conteneur en cours d'exécution
docker container exec -it mysql bash


# Affiche les ports ouverts
docker container port webhost
# Affiche l'adresse IP
docker container inspect --format '{{range .NetworkSettings.Networks}}{{.IPAddress}}{{end}}' webhost

```

### Réseau dans Docker

Le pilote (*driver*) détermine le type de réseau. Principaux types : `bridge`, *user-defined bridge*, `host`, `macvlan`, `ipvlan`, `overlay` et `none`.

```bash
# Crée un réseau bridge défini par l'utilisateur
docker network create my_network
docker network ls
docker container run -d --name new_nginx --network my_network nginx
docker network connect my_network old_nginx
docker network disconnect my_network old_nginx

```


### Système

```bash
# Vérifie l'espace disque utilisé
docker system df

```

### Docker compose

```bash
docker compose up -d  # Lancer les conteneurs.
docker compose up -d --build  # Relancer vos conteneurs en forçant la reconstruction des images.
docker compose logs # Consulter les journaux.
docker compose ps # Lister les conteneurs qui s'exécutent.
docker compose top # Lister les services qui s'exécutent dans les conteneurs.
docker compose down # Arrêter vos conteneurs.
docker compose down --rmi local # Arrêter vos conteneurs et supprimer les images construites localement (--rmi all pour toutes).

```

---

*Version 2026-11-17*  

Avec la collaboration de Jean-Pierre Duchesneau  