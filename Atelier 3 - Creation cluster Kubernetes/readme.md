# Installation Cluster Kubernetes ACS

## Création du cluster avec Azure cli
Une façon très simple d'instancier un cluster Kubernetes sur Azure est d'utiliser Azure-CLI.
Une fois connecté, utiliser la commande suivante

```
az acs create --orchestrator-type kubernetes --resource-group myResourceGroup  --name myK8SCluster --generate-ssh-keys
 ```

## Installation du kubectl
kubectl est l'utilitaire d'administration de votre clsuter Kubernetes. Vous pouvez le télécharger dans les liens que vous trouverez dans le répertoire tools à la racine de ce repo.
Pour ce HoL, il est préférable de l'installer à l'aide de la commande suivante pour avoir la version compatible au mieux avec votre clsuter.

```
az acs kubernetes install-cli --install-location C:\path\kubectl(.exe)
```

PS: Pour les utilisateurs de Windows, nous irons nous connecter en SFTP pour aller récupérer le fichier de config car az cli a un bug. Il faut également lancer azure cli en mode administrateur et sûrement ajouter *c:\program files (x86)* dans le PATH de votre ordinateur.


## Connection à votre cluster
Maintenant que vous avons le cluster kubernetes déployé et l'utilitaire kubctl sur notre poste, il va nous falloir stocker les credentials pour s'y connecter. Pour ce faire, il faut exécuter la commande suivante:

```
az acs kubernetes get-credentials --resource-group myResourceGroup --name myK8SCluster
```

Etape non nécessaire si vous avez récupérer le fichier config en SFTP

## Vérifications
Essayez les commandes suivantes pour valider le bon fonctionnement

```
kubectl get nodes
kubectl get podes --all-namespaces
```

