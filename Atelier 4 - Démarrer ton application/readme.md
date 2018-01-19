# Déploiement de notre application

Les différentes étapes ci-dessous nous mènerons vers une application en production

## Création d'un namespace

Dans Kubernetes, les namespaces sont des regroupements logiques de vos différentes ressources.
Pour ce TP nous allons créer un namespace du nom de votre choix

Afin de créer ce namespace il va vous falloir créer un fichier nommé *namespace.yaml* contenant les informations suivantes:

```
apiVersion: v1
kind: Namespace
metadata:
  name: votingapp
```

Une fois que vous serez connecté avec `kubectl` sur votre cluster nous allons instancier la création du namespace que nous avons défini dans le fichier YAML en utilisant la commande suivante: `kubecl create -f namespace.yaml`
Votre namespace est maintenant créé et prêt à recevoir votre application

## Création du secret pour accéder au repository d'images

L'utilisation d'un registry privé d'images Docker impose que votre Cluster Kubernetes aient les accès pour s'y connecter.
La première chose à faire sur le [portail Azure](https://portal.azure.com) est de mettre de côté les identifiants de connexion si ce n'est pas déjà fait.

Allez dans le resource group créé en début de TP pour héberger votre registry et puis cliquer sur la resource de type `Container Registry`.

Cliquer sur `Access Key` dans le menu de gauche
<image>

Dans la blade de gauche vous avez maintenant toutes les informations pour pouvoir créer le secret dans Kubernetes et profiter de votre registry privé en utilisant la commande suivante:

```
kubectl create secret docker-registry azureregistry --docker-server=<votre_nom_de_registry>.azurecr.io  --docker-username=<votre_nom_de_registry> --docker-password=<<Votre_Mot_de_Passe>  --docker-email=<votre_email> --namespace=azure
```

A noter que l'email ne sert à rien mais est mandatory pour la création du secret, vous ne recevrez pas de spam :-)

## Déploiement de l'application

Pour créer notre application nous allons lancer 4 créations de resources dans Kubernetes:
2 deployments
2 services

Les deployments sont des types de resources Kubernetes qui permettent de scaler le nombre de pods (réplicas) que l'ont veut derrière notre service Kubernetes.

### Deploiement du backend

Pour créer votre Backend, vous allez devoir utiliser kubectl comme auparavant pour lancer la création avec le fichier deployment-back.yaml comme référence.

```
kubectl create -f deployment-back.yaml
```

Une fois ce service déployé, vous avez maintenant vos pods qui tournent sur le cluster, mais votre redis n'est pas accessible car aucun service devant n'est là pour l'exposer au monde, que ce soit local, dans votre cluster ou publiquement.

Afin de créer le servive de votre backend et le rendre accessible par les autres services et/ou pods, exécuter la commande suivante:

```
kubectkl create -f service-back.yaml
```


### Deploiement du frontend

Pour créer votre Backend, vous allez devoir utiliser kubectl comme auparavant pour lancer la création avec le fichier deployment-front.yaml comme référence.

```
kubectl create -f deployment-front.yaml
```

Contrairement au backend ce deployment utilisera les images que vous avez créé sur votre Azure Container Registry. Vous pourrez noter qu'on donne les informations relatives au secret que nous avons également créé pour permettre à Kubernetes d'aller puller les images.

Ensuite, et car nous voulons pouvoir mettre à l'échelle de manière automatique, vous constaterez que nous définissons des contraintes d'utilisations de CPU.

Une fois ce service déployé, vous avez maintenant vos pods qui tournent sur le cluster, mais votre front n'est pas accessible publiquement.

Afin de créer le servive de votre backend et le rendre accessible de l'extéiruer, exécuter la commande suivante qui créera le service et assignera de manière simple un loadbalancer Azure pour répartir la charge entre les pods.

```
kubectkl create -f service-back.yaml
```
