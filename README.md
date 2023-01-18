



<h1 style="color:#0B615E;  text-align:center; vertical-align: middle; padding:40px 0; margin-top:30px " >Cloud computing </br>
Docker Swarm</h1>
             </br>

<h4 style="background-color:#F6CEF5"  id="up-id"> Réalisé par: OUM KOULTHOUME BOUNOUA </h4>


------------

<h4 style="color:#088A85;">   Conditions préalables   </h4>
1.Téléchargemznt et installation Docker Desktop.
</br>
2.La conteneurisation d’une simple application todo-list qui s’exécute dans Node.js.
</br>
3.Configuration de Docker en tapant une invite shell `docker swarm init`
</br>
4.Activer Swarm sur Docker desktop 
</br>

<ul>


<h3 style="color:#58ACFA";>

<h4> <a href="#rep-id">  Conteneuriser une application </a></h4>
On aurez besoin des éléments suivants pour conteneuriser l'application todo-list sur Docker  :
<ul>
<li>Docker s’exécutant localement.
<li>Un client Git.
<li>Le IDE Visual Studio Code
</ul>
<h4>Téléchargement</h4>
  
  Docker desktop

![docker desktop](https://user-images.githubusercontent.com/86807424/213256619-24c075a9-7c93-4afb-96c3-13897161ea38.png)

Avant de pouvoir exécuter l’application, on doit obtenir le code source de l’application. On Clonee le référentiel de mise en route à l’aide de la commande suivante :

````javascript
git clone https://github.com/docker/getting-started.git
````
le contenu du référentiel cloné:


![VsCode](https://user-images.githubusercontent.com/86807424/213255979-53ce4726-5207-4d77-9cb0-d52e0adf667b.png)
 json


<h4>Créer l’image</h4>

Pour créer l’image du conteneur, on va utiliser un fichier texte sans extension de fichier Dockerfile. Un Dockerfile contient un script d’instructions que Docker utilise pour créer une image de conteneur.

On accéde au répertoire getting-started/app et on execute les commandes suivantes.

````javascript
cd getting-started/app 
````

Créer le fichier vide Dockerfile:
````javascript
New-Item -ItemType File -Path .\Dockerfile 
````
![Dockerfile](https://user-images.githubusercontent.com/86807424/213256319-e6fcebd8-a8d0-4ca4-9052-812a69838520.png)


On ajout  le contenu suivant au fichier Dockerfile 

````javascript
# syntax=docker/dockerfile:1
FROM node:18-alpine
WORKDIR /app
COPY . .
RUN yarn install --production
CMD ["node", "src/index.js"]
EXPOSE 3000
````
![Dockerfile content](https://user-images.githubusercontent.com/86807424/213256368-31c30bf3-cf89-46a2-b81f-9ccc88bdda11.png)


Construction de l’image du conteneur avec la commande :
````javascript
docker build -t getting-started .
````
![build image](https://user-images.githubusercontent.com/86807424/213256787-a004f5ce-cafe-4273-87b3-6b3abac96ed2.png)


Le . à la fin de la commande indique à Docker qu’il doit rechercher le dans le répertoire courant. 

La command `docker images` affiche les images construits. 

![docker images](https://user-images.githubusercontent.com/86807424/213256529-d3a186db-6a35-42df-8c21-7aa70a92cd5b.png)



<h4>Start an app container </h4>

Maintenant qu'on a une image, on peut exécuter l’application dans un conteneur. Pour ce faire,on utilise la commande: docker run

démarre notre conteneur à l’aide de la commande et spécifiez le nom de l’image qu'on vient de créer :

````javascript
docker run -dp 3000:3000 getting-started
````
Maintenant dans le vanigateur web  http://localhost:3000. On peut voir notre application:

![localhost3000](https://user-images.githubusercontent.com/86807424/213256900-15a5506a-b288-4c8c-804d-5fb270b78a60.png)


On cliquant Add items, notre frontend stocke avec succès des éléments dans le backend. 


![ADDITEM](https://user-images.githubusercontent.com/86807424/213256928-590d9b13-9656-4a9d-9d15-340ccb348da6.png)


Dans le tableau de bord Docker, on vois le conteneur en cours d’exécution qui utilise l’image et sur le port.getting-started3000


![db](https://user-images.githubusercontent.com/86807424/213258151-7237d2bb-aa8f-4e06-ab22-11198a5e7f70.png)



<h4> <a href="#synthese-id"> Déployer sur Swarm </a></h4>

Dans windows powershell on initialize docker Swarm: docker swarm init 
après avoir le status sur docker system info Swarm: active

#img

Swarm fournit de nombreux outils pour la mise à l’échelle, la mise en réseau, la sécurisation et la maintenance de vos applications conteneurisées, au-delà des capacités des conteneurs eux-mêmes. 

Tous les objets Swarm peuvent et doivent être décrits dans des manifestes appelés fichiers de pile. 

Écrivons un fichier de pile simple pour exécuter et gérer notre application Todo, l’image de conteneur créée dans la partie de conteneurisation. 
   Création de fichier YAML dans le repertoire Getting-started et y mettre le code suivant 
   
   ````javascript
version: '3.7'
services:
  bb-app:
    image: getting-started
    ports:
      - "8000:3000"
   ````
#pdpdp
   
   Déploiment de l'application sur Swarm: 
    ````javascriptdocker stack deploy -c bb-stack.yaml demo 
     ````

#pdjhs

Swarm also creates a Docker network by default to isolate the containers deployed as part of your stack.

   ````javascript
docker service ls
   ````
   
   ------------
   <h3 style="color:#088A85" id="rep-id" >Conteneuriser une application </h3>
Download and install Docker Desktop
![docker desktop](docker desktop.png)






   <h3 style="color:#088A85" id="synthese-id" >Synthèse et analyse spectrale d’une gamme de musique</h3>
<h5 style="color:#FF8000"> Synthèse d’une gamme de musique</h5>
    

--------
 
  <h3> <a href="#up-id"> UP </h3>
  </div>



