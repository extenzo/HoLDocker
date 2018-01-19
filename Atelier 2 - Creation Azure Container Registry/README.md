# Atelier 2 - Creation Azure Container Registry

Afin que les images créées soient disponibles pour les multiples environnements, il est nécessaire de les déposer dans une registry accessible depuis chaque plate-forme.
Il est possible d'utiliser des "Container registry" publique comme celle de Docker, ou bien d'utiliser des "Container Registry" privées.
Dans cet atelier, nous allons voir comment
- Créer une Container Registry privée en utilisant les services Azure ACR "Azure Container Registry"
- Taguer une image afin de la préparer pour le dépôt dans l'ACR
- Exporter l'image vers l'ACR


# Pre requis

Afin de dérouler cet atelier il est nécessaire de :
- Disposer d'un tenant Azure. Pour la création, utiliser le pass fourni pour le HOL
- Installer [Azure CLI 2.0] (https://docs.microsoft.com/en-us/cli/azure/install-azure-cli?view=azure-cli-latest)


# Creation de l'ACR

Comme tout élément créé dans Azure, l'ACR sera membre d'un groupe de ressources. La première chose à faire est donc de créer ce RG :
- Lancer un module Powershell avec les droits administrateur 
- vérifier l'installation d'azure CLI via la commande "az"

.....
Authentification sur le tenant Azure
- Exécuter la commande     "az login" et suivre les instructions

.....
Identification du tenant azure
- Exécuter la commande     "az account list"  pour identifier le ou les tenants auxquels vous etes connectés
- Exécuter la commande     "az account show"  pour identifier le tenant utilisé par défaut

Note si besoin de changer le tenant par défaut, utiliser la commande "az account set"

.....
Création du Groupe de ressources via la commande [az group create] (https://docs.microsoft.com/en-us/cli/azure/group?view=azure-cli-latest#create)
- Exécuter la commande     "az group create <MonGroupeRessource> --location westeurope"

.....
Création de la registry via la commande [az acr create] (https://docs.microsoft.com/en-us/cli/azure/acr?view=azure-cli-latest#create)
- Exécuter la commande     "az acr create --resource-group <MonGroupeRessource> --name <MonAcr> --sku Basic"

.....
Authentification sur la registry
- Exécuter la commande     "az acr login --name <MonAcr>"

.....
Validation 
- Se connecter au portail azure
- Ouvrir le groupe de ressources et valider la présence de l'ACR.
- Observer les paramètres et services disponibles dont celui pour la réplication


#Taguer l'iamage pour son deploiement dans l'ACR

Afin d'identifier la cible quand on publie dans une registry une image de container, il est necessaire que cette dernière soit taguer" avec le nom du serveur de la registry

.....
Identification du serveur de la registry
- Exécuter la commande     "az acr list --resource-group <MonGroupeRessource> --query "[].{acrLoginServer:loginServer}" --output table"

.....
Taguer l'image avec le nom du serveur
- Exécuter la commande     "docker tag azure-vote-front <MonacrLoginServer>/azure-vote-front:redis-v1

.....
Vérifier
- Exécuter la commande     "docker images"
Le résultat doit montrer une image préfixée avec le nom du serveur


# Deployer l'image dans la registry

.....
Publication de l'image

Nous utilisons pour cela la commande [docker push] (https://docs.docker.com/engine/reference/commandline/push/)
- Exécuter la commande     "docker push <MonacrLoginServer>/azure-vote-front:redis-v1

.....
Lister les images dans ACR
- Exécuter la commande     "az acr repository list --name <MonAcr> --output table
 