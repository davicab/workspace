# work
Espaço de trabalho ultilizando docker 


$ docker start container_name
$ docker stop container_name
$ docker restart container_name
$ docker rm container_name
$ docker images
$ docker rmi image_name
$ docker network ls
$ docker network inspect network_name


## # Workspace layers
This layer is dedicated to give us an environment to create our project, we don't depend more any application installed on our S.O, everthing that is necessary is provided through containers.

> ./projects/www put all projects into this folder

##### **PHP**
* on ./projects follow the commands below tor create a php workspace

```
$ docker-compose build --no-cache service_name
$ docker-compose up -d service_name
$ docker attach container_name
```

or 

```
$ docker-compose up -d service_name
$ docker attach container_name