# Lancer l'application Minecraft

Comme vu dans les précédents ateliers, vous devez maintenant déployer l'application Minecraft sur votre cluster.

## Préparation du conteneur

Créer une image Docker à partir du Dockerfile ci-dessous !
Nous sommes là pour vous aider :)

```
FROM ubuntu
RUN apt-get update
RUN apt-get install default-jre wget -y
RUN mkdir /mcserv
WORKDIR /mcserv
RUN wget https://s3.amazonaws.com/Minecraft.Download/versions/1.12.2/minecraft_server.1.12.2.jar && echo eula=true>eula.txt
ENTRYPOINT ["java", "-Xmx1024M -Xms1024M -jar /mcserv/minecraft_server.1.12.2.jar  nogui"] 
```

## A votre tour

1. Pusher l'image sur le registry
2. Créer un deployment et un service pour publier l'application

GOOD LUCK !
