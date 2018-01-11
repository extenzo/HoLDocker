Dans ce lab, vous apprendrez comment créer un container Linux exécutant Minecraft Server. 
Minecraft Server est une application Java, par conséquent, il est possible de l'exécuter sur n'importe quel OS disposant du framework Java. 
1.	Préparation du serveur

Minecraft Server peut être téléchargé a l’[adresse suivante](https://minecraft.net/en-us/download/server). Une fois téléchargé sur un ordinateur exécutant Java, placez le fichier JAR dans un répertoire dédié (par exemple **C:\temp\MCServ**) puis ouvrez une invite de commande, placez-vous dans ce répertoire et lancez la commande suivante  
**java -jar minecraft_server.x.xx.x.jar nogui**
![](https://i0.wp.com/i.imgur.com/3mGBK9Y.png)

Cette commande va initialiser l'environnement du serveur Minecraft mais l'exécution va s'arrêter car c'est la première fois que vous exécutez le serveur et il faut accepter la licence. Pour cela éditez le fichier eula.txt et remplacez la ligne **eula=false** par **eula=true**.

Vérifiez que le serveur est fonctionnel en lançant la commande à nouveau, si vous voyez les informations de création du monde Minecraft (Preparing spawn area), c’est que le serveur est opérationnel.
![](https://i2.wp.com/i.imgur.com/YNJFXLH.png)

2. préparation du conteneur
