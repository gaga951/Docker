### Create a volume called mysql_storage
### whith -d flag container should run in the background
### Name MySQL container called db-app
### Use the mount flag to mount the mysql_storage volume to /var/lib/mysql
### Use the -e flag to set MYSQL_ROOT_PASSWORD to DPdbpasshear

$ docker volume create mysql_storage

$ docker container run -d --name db-app \
 --mount type=volume,source=mysql_storage,target=/var/lib/mysql \
 -e MYSQL_ROOT_PASSWORD=DPdbpasshear \
 mysql:latest
 

### let's look at the container"

$ docker container inspect app-database
