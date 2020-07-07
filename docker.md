Docker
===

## Docker Search
Search a container

        docker search <CONTAINER> --no-trunc
---
## Docker Run

Create and run simple container

        docker run -it --name <CONTAINER_NAME> CONTAINER

Option

        -d Detach mode
        -e <ENV_NAME>=<VALUE> Set environment variable
        -i Interactive mode
        -p <HOST_PORT>:<CONTAINER_PORT> Expose port
        -v <LOCAL_PATH>:<CONTAINER_PART> Bind mount volumn
        -t Allocate a pseudo-tty
        --name <CONTAINER_NAME> Set Container name
        --link Link to another Container

Example

        docker run -it --name test-container ubuntu
        docker run --name test-db -e MYSQL_ROOT_PASSWORD=mypassword -d -p 3306:3306 mysql
        docker run --name test-site --link test-db:mysql -p 3000:80 -d -v /Users/arnonpuitrakul/Documents/test_site:/var/www/html/ php:7-apache
---
## Docker Basic command

List currently running docker containers:

    docker ps

List all docker containers (running and stopped):

    docker ps -a

Start a container from an image, with a custom name:

    docker run --name container_name image

Start or stop an existing container:

    docker start|stop container_name

Pull an image from a docker registry:

    docker pull image

Open a shell inside of an already running container:

    docker exec -it container_name sh

Remove a stopped container:

    docker rm container_name

---
## Create a Docker Image

        docker commit <CONTAINER> <IMAGENAME>

## Push to DockerHub
```
docker login -u <USERNAME>
docker tag <CONTAINER> <USERNAME>/<DOCKER_REPO>:<TAG>
docker push <USERNAME>/<DOCKER_REPO>:<TAG>
```

---
## docker-compose

List all running containers:

        docker-compose ps

Create and start all containers in the background using a `docker-compose.yml` file from the current directory:

        docker-compose up 

run command in the container

        docker-compose exec <CONTAINER> bash

Start all containers using an alternate compose file:

        docker-compose --file path/to/file up

Stop all running containers:

        docker-compose stop

Stop and remove all containers, networks, images, and volumes:

        docker-compose down --rmi all --volumes

Follow logs for all containers:

        docker-compose logs --follow