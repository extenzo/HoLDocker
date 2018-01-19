# Création d'un Namespace

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

Vous pouvez également directement appeller le fichier hébergé sur github `kubectl create -f https://raw.github.....`

Votre namespace est maintenant créé et prêt à recevoir votre application
