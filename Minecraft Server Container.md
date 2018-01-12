Dans ce lab, vous apprendrez comment créer un container Linux exécutant Minecraft Server. 
Minecraft Server est une application Java, par conséquent, il est possible de l'exécuter sur n'importe quel OS disposant du framework Java. 
1. prérequis

Disposer d'une machine exécutant docker avec des conteneurs Linux. Par exemple en utilisant le modèle de machine virtuelles [Docker on Ubuntu Server](https://azuremarketplace.microsoft.com/en/marketplace/apps/CanonicalandMSOpenTech.DockerOnUbuntuServer1404LTS/) disponible sur le marketplace Azure. 

2. Préparation du conteneur

Lancez une invite de commande en mode administrateur/root puis tapez la commande suivante pour exécuter un conteneur ubuntu en mode interactif
```
docker run -t -i ubuntu /bin/bash
```

Puis tapez les commandes suivantes pour installer Java, télécharger et configurer le serveur Minecraft
```
export LANG=C
apt-get update
apt-get dist-upgrade
apt-get install default-jre
apt-get install wget
mkdir /mcserv
cd /mcserv
wget https://s3.amazonaws.com/Minecraft.Download/versions/1.12.2/minecraft_server.1.12.2.jar
echo eula=true>eula.txt
exit
```

Il faut maintenant sauvegarder les changements, pour cela, récupérez d'abord le nom du conteneur en tapant

```
docker ps -a
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS                       PORTS               NAMES
8da0e45098b2        ubuntu              "/bin/bash"         2 hours ago         Exited (130) 2 minutes ago                       **zealous_noyce**
```

Puis 

```
docker commit zealous_noyce minecraftserver:1.12.2
```

Votre nouvelle image apparait maintenant dans la liste des images disponibles

```
docker images
REPOSITORY          TAG                 IMAGE ID            CREATED              SIZE
minecraftserver     1.12.2              38f50e621a37        About a minute ago   474MB
ubuntu              latest              00fd29ccc6f1        3 weeks ago          111MB
```

Vous pouvez maintenant tester votre conteneur en tapant
```
docker run -w /mcserv minecraftserver:1.12.2 java -Xmx1024M -Xms1024M -jar /mcserv/minecraft_server.1.12.2.jar  nogui
```
