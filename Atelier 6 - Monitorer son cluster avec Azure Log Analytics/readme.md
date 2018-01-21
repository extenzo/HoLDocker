# Deployer OMS

[Azure Log Analytics] (https://docs.microsoft.com/fr-fr/azure/log-analytics/) est une service Azure, disponible en stand alone, via un package ou via la suite Operations Management Suite
Voir le lein vers [OMS] (https://docs.microsoft.com/fr-fr/azure/operations-management-suite/operations-management-suite-overview)

Le but de cet atelier est de manipuler Azure log analytics afin de 
- Créer un espace de travail
- Déployer le solution pack [Container Monitoring] (https://docs.microsoft.com/fr-fr/azure/log-analytics/log-analytics-containers)
- Configurer un agent pour ACS
- Exminer les informations remontées via la supervision

Ensuite, pour déployer les agents OMS qui permettront d'aller collecter les données pour les afficher le portail de Log Analytics.
Nous allons utiliser les DeamonSets qui permettent d'aller déployer un pod sur chaque noeud de mon cluster.

Pour ceci, vous prenez le fichier install-OMS.yaml présent dans ce répertoire et vous exécutez la commande suivante en ayant bien pris soin de cliquer sur la roue crantée pour récupérer le Workspace ID et une des clefs pour remplacer les valeurs dans le fichier yaml.

```
kubectl create -f install-OMS.yaml
```

# Pre requis
Avoir terminer les ateliers 1, 2 et 3
