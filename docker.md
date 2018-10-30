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
## Docker Start

Run an existing container

        docker start [CONTAINER_ID|CONTAINER_NAME] -i
