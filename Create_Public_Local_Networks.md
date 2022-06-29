### create a bridge network called frontend that will be publicly accessible:

$ docker network create frontend

### create a second bridge network called localhost that will be internal:

$ docker network create localhost --internal

### Create a MySQL container called database in localhost network with mysql image

$ docker container run -d --name database \
 --network localhost \ 
 -e MYSQL_ROOT_PASSWORD=P4ssW0rd0! \
 mysql:5.7
 
Create an Nginx container "front-app" and publish port 80 on the host to port 80 on the container. 
attach container to both networks

$ docker container run -d \ 
 --name front-app \
 --network frontend  \
 nginx:latest
 
### Connect front-app to the internal network
Nginx container is created, and is connected to the internet, we've got to connect it to the localhost network. 
To make sure both containers are running, run a quick 

$ docker container ls. 

### Once we're sure they're up, we can do the actual connecting:

$ docker network connect localhost front-app

### let's look at the container front-app:

$ docker container inspect front-app
