# Stockage des identifiants pour Azure Container Registry

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