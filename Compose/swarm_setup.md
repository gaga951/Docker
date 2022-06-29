Request join token On the "Master" node by command

$ docker swarm join-token worker

run the join token on the "Worker" node

$ docker swarm join --token tokenexamplecode master_IP:2377

Check from "Masetr" we should see two nodes each with Ready STATUS and Availability must be Active.
$ docker node ls


Create and Run Compose File from "Master" node

$ docker stack deploy --compose-file docker-compose.yml wp-site

Check it by commands

$ docker stack ls

$ docker service ls
