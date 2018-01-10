# VOTING APP

Pour créer notre application nous allons lancer 4 créations de resources dans Kubernetes:
2 deployments
2 services

Les deployments sont des types de resources Kubernetes qui permettent de scaler le nombre de pods (réplicas) que l'ont veut derrière notre service Kubernetes.

## Deploiement du backend

Pour créer votre Backend, vous allez devoir utiliser kubectl comme auparavant pour lancer la création avec le fichier deployment-back.yaml comme référence.

```
kubectl create -f deployment-back.yaml
```

Une fois ce service déployé, vous avec maintenant vos pods qui tournent sur le cluster, mais votre redis n'est pas accessible car aucun service devant n'est là pour l'exposer au monde, que ce soit local, dans votre cluster ou publiquement.

Afin de créer le servive de votre backend et le rendre accessible par les autres services et/ou pods, exécuter la commande suivante:

```
kubectkl create -f service-back.yaml
```


## Deploiement du frontend

Pour créer votre Backend, vous allez devoir utiliser kubectl comme auparavant pour lancer la création avec le fichier deployment-front.yaml comme référence.

```
kubectl create -f deployment-front.yaml
```

Contrairement au backend ce deployment utilisera les images que vous avez créé sur votre Azure Container Registry. Vous pourrez noter qu'on donne les informations relatives au secret que nous avons également créé pour permettre à Kubernetes d'aller puller les images.

Ensuite, et car nous voulons pouvoir mettre à l'échelle de manière automatique, vous constaterez que nous définissons des contraintes d'utilisations de CPU.

Une fois ce service déployé, vous avec maintenant vos pods qui tournent sur le cluster, mais votre front n'est pas accessible publiquement.

Afin de créer le servive de votre backend et le rendre accessible par les autres services et/ou pods, exécuter la commande suivante:

```
kubectkl create -f service-back.yaml
```