# dockerExam
Exercice 01:
1- Clone un projet 
 => git clone https://github.com/brik-50/dockerExam.git
2- Creation de dockerfile 
  => 
FROM node:21-alpine
WORKDIR /app
COPY ./package*.json ./
RUN npm install
COPY . .
EXPOSE 3000
CMD ["node", "server.js"]

3- Creation de l'image
 => docker build -t docker_examen_nodejs .
4 - Lancement de conteneur
  => docker run -d --name conteneur_docker_examen_nodejs -p 8081:80 docker_examen_nodejs

Exercice 02 :
Telechargement des 3 images 
 - docker pull mysql:8.0.28
 - docker pull makouz/tuto_backend:1.0.0
 - docker pull makouz/tuto_front:1.0.0

 1- Communication des 3 parties (images)
  - docker network create connection_trois_conteneur
 2 - Spécification de BD
  - docker run -d --name mysql --network connection_trois_conteneur -e MYSQL_DATABASE=testdb -e MYSQL_ROOT_PASSWORD=joelson mysql:8.0.28

5- Mapping de port 8088 vers le port 2222 pour le server backend 
- docker run -d --name backend --network connection_trois_conteneur -p 2222:8080 -v backend_data:/path/in/container makouz/tuto_backend:1.0.0
6 - 
- docker run -d --name frontend --network connection_trois_conteneur -p 8088:80 makouz/tuto_front:1.0.0

Exercice 03 :
Refaisons la même chose avec un fichier docker-compose.yaml
- Donc, il faut utiliser la commande 
 - docker-compose up -d
