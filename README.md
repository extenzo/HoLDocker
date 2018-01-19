# HoLDocker

L'obectif de ce Hands On Lab est de vous faire découvrir le voyage d'une application depuis un environnement de développement local, jusqu'à sa mise en production dans Azure.
Afin de garantir une conformité des environnements de bout en bout ainsi qu'une facilité de déploiement, mise à l'échelle et retour arrière éventuels
nous allons nous appuyer pour cela sur la technologie des containers

Dans un premier temps une application de sondage sera utilisée. Elle est composée d'un module front et d'un module back.
Puis une fois les différents concepts parcourus, il sera temps de passer aux choses sérieuse avec MineCraft

Description des ateliers
- Atelier 1 : Déployer l'application de sondage dans l'environnement Docker local (voir les outils indispensables pour le lab en fin de document) et manipuler les commandes de base de Docker
- Atelier 2 : Créer une Container Registry dans Azure et exporter les images
- Atelier 3 : Création d'un cluster Kubernetes dans Azure et déploiement de l'application
- Atelier 4 : Manipulation des outils Kubernetes en particulier pour les fonctions de mise à l'échelle
- Atelier 5 : Mise en oeuvre de la supervision via Azure Log Analytics
- Atelier 6 : Création d'un container pour exécuter MineCraft et utilisant de l'infrastructure créée dans les ateliers précédents pour le faire exécuter au sein du cluster Kubernetes



# Quelques outils indispensables pour le Hands On Lab :

1.  Si vous ne disposez pas de Docker sur votre pc, vous pouvez télécharger [Docker for Windows ](https://store.docker.com/editions/community/docker-ce-desktop-windows). Cet outil est indispensable pour la suite du TP
2. Indispensable également pour la suite du TP, l'utilitaire qui nous permettra d'administrer notre cluster Kubernetes. Les instructions pour l'installation sont disponibles sur ce lien [Kubectl cmd line tool](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-kubectl-binary-via-curl)
3. Nous vous proposons d'utiliser [Visual Studio Code](https://code.visualstudio.com/download) comme éditeur pour les différents fichiers que nous aurons à créer/modifier. Vous pouvez bien sur utiliser votre ISE/IDE favori
4. Et enfin, l'outil qui sera la base de toutes nos opérations pour intéragir avec vos abonnement Azure, [Azure CLI] (https://docs.microsoft.com/fr-fr/cli/azure/install-azure-cli?view=azure-cli-latest)

