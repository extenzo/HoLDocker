# Deployer OMS

Tout d'abord il va nous falloir un compte OMS.
Deux options:
1. portal.azure.com > Log Analytics > Créer
2. https://www.mms.microsoft.com/Workspace

Ensuite, pour déployer les agents OMS qui permettront d'aller collecter les données pour les afficher le portail de Log Analytics.
Nous allons utiliser les DeamonSets qui permettent d'aller déployer un pod sur chaque noeud de mon cluster.

Pour ceci, vous prenez le fichier install-OMS.yaml présent dans ce répertoire et vous exécutez la commande suivante en ayant bien pris soin de cliquer sur la roue crantée pour récupérer le Workspace ID et une des clefs pour remplacer les valeurs dans le fichier yaml.

```
kubectl create -f install-OMS.yaml
```


