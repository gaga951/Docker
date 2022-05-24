### To get all version information of the client and server is the

$ docker version

### To get only the server version details
$ docker version --format '{{.Server.Version}}'

### There are many publicly available images that we can use to work with Docker.

$ docker pull hello-world

### To list downloaded docker images

$ docker images

### To create a container from an image use

$ docker create hello-world

### To run a container use the 

$ docker container start examplecontainer

### The -i runs the container interactively and allows us to see the output

$ docker container start -i examplecontainer

### This will create a new container for an image and run it

$ docker run hello-world


### -d means the container needs to start in the detached mode.
Detached mode, started by the option --detach or –d flag in docker run command, means that a Docker container runs in the background of your terminal. 
It does not receive input or display output. Using detached mode also allows you to close the opened terminal session without stopping the container.

$ docker run -it -d <image_name>


### To see what images are already installed on your machine use

$ docker image ls


### To list the containers that we have built: docker container ls. The -a flag allows us to see both stopped and running containers.

$ docker container ls –a

### Running containers interactively allows you to run commands inside the container if it supports it.

$ docker run -it openjdk

### To see what containers are currently running

$ docker ps

### Container level logging can be done using the command: 
$ sudo docker run –it <container_name> /bin/bash

### example of accessing Interactive shell

$ docker run -it ubuntu bash

### The exec command lets you get inside a container and work with it

$ docker exec -it containerid bash

## -i : interactive or STD_IN
## -t : terminal or STD_OUT


### In order to check for the container level logs, we can run the command:

sudo docker logs <container_id>


# gives the config and meta data used to start this container; returns JSON array

$ docker container inspect container-id

### Logs

$ docker container logs container_name

$ docker container logs -f container_name
  
### Lists specific processes in a specific container
  
$ docker top containername
  
### Get CPU, Mem usage of the container
  
$ docker container stats containername



### To build a docker image using a Dockerfile we can use the docker image build command and provide it the directory where the Dockerfile exists. The --tag option allows us to name and tag the docker image.

$ docker image build . --tag "dockerimagename:version"

### To run docker compose file 

$ docker-compose up

### In order to run docker-compose with JSON

$ docker-compose -f docker-compose.json up

### The docker-compose stop command will stop your containers, but it won't remove them. 
$ docker-compose stop

### Stop Containers using compose file
### will stop your containers, but it also removes the 

$ docker-compose down

### To remove all unused docker resources

$ docker system prune --all

### To Start or Stop single or multiple docker containers

$ docker stop containername

$ docker start containername

### To kill a container use

$ docker kill container_id

### The images can be pushed to Docker Hub through the

$ docker push


### To export a docker image as an archive use

$ docker save -o exported_name.tar container-name
  
### To import a pre-exported Docker image into another Docker host use
  
$ docker load -i <export_image_name>.tar

### for syncing a directory of a container with any of the host directories
### The belove command mounts the directory /data/app in the host to the usr/src/app directory. 
### We can sync the container with the data files from the host without having the need to restart it.
### This also ensures data security in cases of container deletion.

$ docker run -v /data/app:usr/src/app myapp

############################################
## Where are docker volumes stored in docker?

### Volumes are created and managed by Docker and cannot be accessed by non-docker entities. 
### They are stored in Docker host filesystem at /var/lib/docker/volumes/
############################################

### Information about Docker installed on the host system.
### The information can be like what is the number of containers or images and in what state they are running and hardware specifications like total memory allocated, speed of the processor, kernel version, etc

$ docker info

### To login to the docker registry

$ docker login

### push image to docker hub

$ docker push username/image name

### edit  and update container

$ docker commit conatainer id username/imagename


### Docker gives 3 default networks: bridge, none and host. When you start Docker, a default bridge network (also called bridge) is created automatically, and newly-started containers connect to it unless otherwise specified.

$ docker network ls

$ docker network inspect bridge
  
### Docker Networking: Port Mapping

$ docker run –p 80:5000 nginx  (in this case 5000 is Container port)

## Docker Volumes commands
### Create a volume
$ docker volume create      

### Display detailed information on one or more volumes
$ docker volume inspect     

### List volumes
$ docker volume ls          

### Remove all unused local volumes
$ docker volume prune       

### Remove one or more volumes
$ docker volume rm          

######################################################

## container restart by itself while using certain docker-defined policies while using the $ docker run command. 
### Following are the available policies:

1. Oﬀ: In this, the container won’t be restarted in case it's stopped or it fails.
2. On-failure: Here, the container restarts by itself only when it experiences
failures not associated with the user.
3. Unless-stopped: Using this policy, ensures that a container can restart only
when the command is executed to stop it by the user.
4. Always: Irrespective of the failure or stopping, the container always gets
restarted in this type of policy.

$ docker run -dit — restart [restart-policy-value] [container_name]


######################################################
# To delete all containers including its volumes use:

docker rm -vf $(docker ps -aq)

### To delete all the images use:

docker rmi -f $(docker images -aq)

Remember, you should remove all the containers before removing all the images from which those containers were created.

### For Windows (power shell, not cmd)

In case you are working on Windows (Powershell),

$images = docker images -a -q
foreach ($image in $images) { docker image rm $image -f }

Based on the comment from CodeSix, one liner for Windows Powershell,

docker images -a -q | % { docker image rm $_ -f }
For Windows using command line,

for /F %i in ('docker images -a -q') do docker rmi -f %i

###########################################################

