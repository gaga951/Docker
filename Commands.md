######################################################
# To delete all containers including its volumes use,

docker rm -vf $(docker ps -aq)
To delete all the images,

docker rmi -f $(docker images -aq)
Remember, you should remove all the containers before removing all the images from which those containers were created.

For Windows (power shell, not cmd)

In case you are working on Windows (Powershell),

$images = docker images -a -q
foreach ($image in $images) { docker image rm $image -f }
Based on the comment from CodeSix, one liner for Windows Powershell,

docker images -a -q | % { docker image rm $_ -f }
For Windows using command line,

for /F %i in ('docker images -a -q') do docker rmi -f %i

###########################################################


There are many publicly available images that we can use to work with Docker.
$ docker pull hello-world

To list downloaded docker images
$ docker images

To create a container from an image use
$ docker create hello-world

To run a container use the 
$ docker container start examplecontainer

The -i runs the container interactively and allows us to see the output
$ docker container start -i examplecontainer

This will create a new container for an image and run it
$ docker run hello-world

To see what images are already installed on your machine use
$ docker image ls


To list the containers that we have built: docker container ls
The -a flag allows us to see both stopped and running containers.
$ docker container ls –a

Running containers interactively allows you to run commands inside the container if it supports it.
$ docker run -it openjdk

To see what containers are currently running
$ docker ps

Interactive shell
$ docker run -it ubuntu bash

To build a docker image using a Dockerfile we can use the docker image build
command and provide it the directory where the Dockerfile exists. The --tag
option allows us to name and tag the docker image.
$ docker image build . --tag "dockerimagename:version"

To run docker compose file 
$ docker-compose up

Stop Containers
$ docker-compose down

To remove all unused docker resources
docker system prune --all


