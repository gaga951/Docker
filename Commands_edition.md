### Shows all images
$ docker images

### create an images from a tarball

$ docker import

### creates image fro Dockerfile

$ docker build

### Creates image from a container, pausing it temprorarly if its running

$ docker commit

### Removes an Image

$ docker rmi

### Loads an image from a tar archive as STDIN, including images and tags.

$ docker load

### Saves an image to a tar archive as STDN, including images and tags.
$ docker save


## Informational
### Shows history of images

$ docker history

### Tags an image to a name

$ docker tag

### Shows running containers

$ docker ps

### Gets logs from container

$ docker logs

### Looks at all the info on a container

$ docker inspect

### Gets events from container

$ docker events

### Shows public facing port of container

$ docker port

### Show running processes in container

$ docker top

### Shows containers resource usage statistics

$ docker stats

### shows changed files in the container's FS

$ docker diff

### Import/Export comands

### Copies files or folders between a container and the local filesystem.

$ docker cp

### Turns container filesystem inot tarball archive stream to STDOUT

$ docker export

### To execute a command in container

$ docker exec

$ docker run options IMAGE Non_Default_CMD CMD_Args

  -d, --detach                         Run container in background and print container ID
  
  -e, --env list                       Set environment variables
  
  -h, --hostname string                Container host name
  
  -i, --interactive                    Keep STDIN open even if not attached
  
  -l, --label list                     Set meta data on a container
  
  --log-driver string              Logging driver for the container
      
  -p, --publish list                   Publish a container's port(s) to the host
  
  -P, --publish-all                    Publish all exposed ports to random ports
  
  -t, --tty                            Allocate a pseudo-TTY
  
  -u, --user string                    Username or UID (format: <name|uid>[:<group|gid>])
  
  -v, --volume list                    Bind mount a volume
  
  -w, --workdir string                 Working directory inside the container
  
  --entrypoint string              Overwrite the default ENTRYPOINT of the image


