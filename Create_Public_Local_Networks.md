### create a bridge network called frontend that will be publicly accessible:

$ docker network create front_net

### create a second bridge network called local_net that will be internal:

$ docker network create local_net --internal

### Create a MySQL container called database in local_net network with mysql image

$ docker run -d --name database --network local_net -e MYSQL_ROOT_PASSWORD=dbpassgoeshear mysql:5.7
 
Create an Nginx container "front-app" and publish port 80 on the host to port 80 on the container. 
attach container to both networks

$ docker run -d --name front-app --network front_net nginx:latest
 
### Connect front-app to the internal network
Nginx container is created, and is connected to the internet, we've got to connect it to the local_net network. 
To make sure both containers are running, run a quick 

$ docker container ls. 

### Once we're sure they're up, we can do the actual connecting:

$ docker network connect local_net front-app

### let's look at the container front-app:

$ docker container inspect front-app
