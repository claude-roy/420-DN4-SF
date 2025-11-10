# Aide mémoire

---
**NOTE**

Ceci est un aide mémoire et non un cours ni une liste exhaustive de commandes à connaître pour un examen.

---

##Linux 
### Les incontournables

| Commande |  Courte description |
|---|---|
| man | Manuel |
| pwd | Affiche le répertoire courant |
| ls | Liste les fichiers (-a affichage des fichiers cachés, -l affichage long) |
| cd | Change le répertoire courant |
| cat | Concatène des fichiers vers la sortie |
| less | Affiche et pagine un fichier |
| touch | Création / MAJ dates de fichiers |
| head / tail | Affiche le début / fin d'un fichier |
| grep | Recherche un motif dans un fichier |
| locate | Recherche de fichiers à partir d'une base de données |
| find | Recherche de fichiers à partir du système de fichiers |
| mount | Crée un point de montage |
| diff | Compare des fichiers entre eux |
| cal | Affiche un calendrier |
| wget / curl | Effectue une requête web |
| echo | Affiche un message |
| sudo | Exécute une commande avec les privilèges administrateur |
| su | Change l'utilisateur courant pour celui voulu (root par défaut) |

### Git

| Commande |  Courte description |
|---|---|
| git init | Initialise un dépot Git |
| git clone | Clone un dépot Git distant |
| git add | Ajoute un fichier dans le suivi |
| git status | Affiche le status du dépot |
| git commit | Valide les modifications |
| git pull | Récupère les modifications distantes |
| git push | Envoie les modifications locales vers le dépot distant |

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
| mv | Déplacement de fichiers / répertoire |
| rm | Supprime un fichier / répertoire |
| ln | Crée un lien vers un fichier |

#### Droits sur les fichiers

| Commande |  Courte description |
|---|---|
| chmod | Modifie les accès à un fichier pour l'utilisateur, le groupe et les autres |
| chown | Modifie le propriétaire d'un fichier |
| chgrp | Modifie le groupe d'un fichier |

### Gestion des processsus

| Commande |  Courte description |
|---|---|
| ps | Affiche les processus |
| top | Affiche les processus en temps réel |
| kill | Arrête un processus |

### Gestion du noyau et des modules

| Commande |  Courte description |
|---|---|
| lsmod | Afficher l'état des modules dans le noyau Linux  |
| modprode | Ajouter et supprimer des modules du noyau Linux  |
| modinfo | Afficher des informations sur un module du noyau Linux  |



### Commande réseau

| Commande |  Courte description |
|---|---|
| ip addr show / ip a | Affiche les adresses IPs |
| ip addr show dev enp0s3 | Affiche l'adresses IP de l'interface enp0s3 |
| ip link show | Affiche les interfaces réseaux |
| sudo ip link set enp0s3 up/down | Active / désactive un interface réseau |
| ip route | Affiche la table de routage |
| ping | Effectue une suite de requêtes ICMP |
| nslookup | Interroge le serveur DNS |
| sudo nft | Affiche / configure les règles du coupe-feu |
| traceroute | Affiche les noeuds traversés vers une destination |

## Docker
### Installation
Installer Docker Linux:  

```docker
curl -sSL https://get.docker.com/ | sh
```

### Container

```docker
docker container run -d --publish 8080:80 --name webhost nginx
docker container top webhost
docker container inspect webhost
docker container stats webhost

#Open a shell in a new container
docker container run -it --name proxy nginx bash
docker container run -it alpine sh
#Relance un container avec shell interactif
docker container start -ai ubuntu
#Open shel in a running container
docker container exec -it mysql bash


#Afficher les ports ouverts
docker container port webhost
#Affciher Adresse IP
docker container inspect --format '{{ .NetworkSettings.IPAddress }}' webhost

```

### Réseau dans docker
```docker
# Informations
driver = network type
Network type = bridge, user-defined bridge, host, macvlan

# Create a user-defined bidge
docker network create my_network
docker network ls
docker container run -d --name new_nginx --network my_network nginx
docker network connect my_network old_nginx
docker network disconnect my_network old_nginx

```


### System

```docker
# Vérifie l'espace disque utilisé
docker system df

```

### Docker compose

```docker
docker compose up -d  # Lancer les conteneurs.
docker compose up -d --build  # Relancer vos conteneurs en forçant la reconstruction des images.
docker compose ps  # voir les conteneurs qui s'exécutent
docker compose logs # Consulter les journaux.
docker compose ps # Lister les conteneurs qui s’exécutent.
docker compose top # Lister les services qui s’exécutent dans les conteneurs.
docker compose down # Arrêter vos conteneurs.
docker compose down --rmi local # Arrêter vos conteneurs et effacer les images.

```


Jean-Pierre Duchesneau  
Claude Roy