# Atelier 4 - Mise à l'échelle

Le but de cet atelier est de manipuler les pods Kubernetes afin de mettre à l'échelle l'environnement en fonction des besoins de performances.
Dans un premier temps, nous utiliserons les fonctions manuelles, puis dans un second temps nous configurerons l'environnement pour une mise à l'échelle automatique en fonction de la charge CPU


# Pre requis
Avoir terminer les ateliers précédents


#Mise à l'échelle manuellement
.....
Identifier les pods
- Exécuter la commande     "kubectl get pods"

.......
Augmenter le nombre de pods :
- Exécuter la commande     "kubectl scale --replicas=5 deployment/azure-vote-front"

......
Valider :
- Exécuter la commande     "kubectl get pods"



#mise à l'echelle manuelle
......
Identification des paramètres dans le fichier yaml
- Editer le fichier deployement-front.yaml
- Localiser la zone contenant les paramètres "cpu"

.....
Utilisation de la commande [kubectl autoscale] (https://kubernetes.io/docs/tasks/run-application/horizontal-pod-autoscale/)
- Executer la commande       "kubectl autoscale deployment azure-vote-front --cpu-percent=50 --min=3 --max=10"
- Executer la commande       "kubectl get hpa"