# Utilisation de l'environnement Docker local pour déploiement de l'application

Si ce n'est déjà fait, installez l'application Docker
- Pour environnement [Windows] (https://docs.docker.com/docker-for-windows/)
- Pour environnement [Mac] (https://docs.docker.com/docker-for-mac/)

L'application azure-voting-app-redis s'appuie sur des images de base Linux.
Si vous utilisez Docker for Windows : Il faut s'assurer que l'environnement Docker local est bien configuré pour ce mode :

- Dans la barre des tâches, clic droit sur l'icone Docker
- Vérifier que le mode Linux est utilisé (c'est le cas si la ligne "switch to Windows Containers apparait")


# Utilisation de la ligne de commande Docker
- lancer un module Powershell avec les droits administrateurs et exécuter les commandes suivantes :
- Exécuter la commande     "docker --version" pour valider la version installée
- Exécuter la commande     "docker info   afin de valider le fonctionnement du Docker Engine, sa version et identifier les containers en cours d'exécution
- Exécuter la commande     "docker run hello-world" afin de tester l'environnement via une première image
- Exécuter la commande     "docker images"   pour identifier les images de containers disponibles localement 
- Exécuter la commande     "docker search redis"   afin de rechercher dans les container registry publique les images linux + redis

Autres commandes basiques que nous utiliserons plus tard :
- "docker pull <monimage>" pour charger une image dans le cache local
- "docker push <monserveurregistry>/<monimage>" pour uploader une image locale dans une registry
- "docker run" pour exécuter un container de manière isolée
- "docker-compose <monfichieryml>" outil pour définir et exécuter une application basée sur plusieurs containers  

# définition et creation de l'application
L'application de sondage s'appuie sur deux containers : un front et un back. La description de l'application est contenue dans le fichier "docker-compose.yml"

- ouvrir le fichier avec un éditeur de texte et parcourir ses différentes sections

- Exécuter la commande     "docker-compose up -d" depuis le dossier contenant le fichier "docker-compose.yml"

- Une fois la commande terminée, lancer "docker images"

On remarque que trois images ont été téléchargée ou créées 

- Exécuter la commande    "docker -ps" afin d'identifier les containers en cours d'exécution

- Exécuter la commande    "docker inspect azure-vote-front" et rechercher la valeur du "HostPort" dans la section "Network settings". Cela indique le port exposé par l'application

- Tester l'application deuis un navigateur via l'URL "http://localhost:8080"

