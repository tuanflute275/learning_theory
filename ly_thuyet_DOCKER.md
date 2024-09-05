# Dokcer Theory 

## Pull 2 images 
    docker pull mcr.microsoft.com/mssql/server:2019-CU15-ubuntu-20.04
---
    docker pull mcr.microsoft.com/mssql/server:2017-CU28-ubuntu-16.04
---
    tag = version
    Create containers from images
    1 image => multiple containers
    -d : Detach(background) mode
    -e: environment variables
    --name : container's name
    -p: map port

MacOS/Linux:

    docker run \
    -e "ACCEPT_EULA=Y" \
    -e "SA_PASSWORD=Abc@123456789" \
    --name sql-server-2019-container \
    -p 1435:1433 \
    -v /Users/hoangnd/Desktop/temp:/var/opt/mssql \
    -d mcr.microsoft.com/mssql/server:2019-CU15-ubuntu-20.04

Docker container with default volume
MacOS/Linux:

    docker run \
    -e "ACCEPT_EULA=Y" \
    -e "SA_PASSWORD=Abc@123456789" \
    --name sql-server-2019-container \
    -p 1435:1433 \
    -v my-volume-1:/var/opt/mssql \
    -d mcr.microsoft.com/mssql/server:2019-CU15-ubuntu-20.04

Windows:

    docker run ^
    -e "ACCEPT_EULA=Y" ^
    -e "SA_PASSWORD=Abc@123456789" ^
    --name sql-server-2019-container ^
    -p 1435:1433 ^
    -v my-volume-1:/var/opt/mssql ^
    -d mcr.microsoft.com/mssql/server:2019-CU15-ubuntu-20.04

    Volume's path in Host(your PC, laptop):
    ls -la ~/Library/Containers/com.docker.docker/Data/vms

In Windows:

    \\wsl$\docker-desktop-data\version-pack-data\community\docker\volumes

## remove container => data lost => how to solve ?
Let's map container's volume to your host(PC)'s volume

    docker rm 
    -f: force
    -v "host' volume":"container's volume" 

Create a container for mysql:

Windows:

    docker run ^
    -e MYSQL_ROOT_PASSWORD=Abc@123456789 ^
    --name mysql8-container ^
    -p 3308:3306 ^
    -v mysql8-volume:/var/lib/mysql ^
    -d mysql

MacOS(Linux):

    docker run \
    -e MYSQL_ROOT_PASSWORD=Abc@123456789 \
    --name mysql8-container \
    -p 3308:3306 \
    -v mysql8-volume:/var/lib/mysql \
    -d mysql

Go inside the container:

- -it = interactive mode
- docker exec -it mysql8-container bash
- Then:
- mysql -u root -p


## App with multiple containers:
    docker network create todo-app-network
---
    docker run -d \
    --name mysql-container \
    --network todo-app-network \
    --network-alias todo-app-network-alias \
    -v todo-mysql-database:/var/lib/mysql \
    -e MYSQL_ROOT_PASSWORD=Abc@123456789 \
    -e MYSQL_DATABASE=todoDB \
    -d mysql
---
    docker exec -it mysql-container mysql -u root -p

Create another container, has the same network
it = interactive mode

    docker run -it \
    --network todo-app-network \
    --name netshoot-container \
    nicolaka/netshoot

>dig = DNS lookup utility
>dig todo-app-network-alias

Create another nodeJS container:
- -w: working directory

pwd : current folder

    docker run -dp 8002:8000 \
    --name todo-app-container \
    -w /app -v "$(pwd):/app" \
    --network todo-app-network \
    -e MYSQL_HOST=todo-app-network-alias \
    -e MYSQL_USER=root \
    -e MYSQL_PASSWORD=Abc@123456789 \
    -e MYSQL_DB=todoDB \
    node \
    sh -c "yarn install && yarn run:dev"

>docker logs todo-app-container

- npm init -y
- yarn add ronin-server ronin-mocks
- npm install -g nodemon

> You should create your own "custom image"

> need a configuration file => Dockerfile 
"custom image" must based on an "existing image"

Build image from Dockerfile

docker build --tag node-mysql-image .

Rename your image:

docker tag node-mysql-image:latest node-mysql-image:v1.0.0

Remove unnecessary image(rmi = remove image):

docker rmi node-mysql-image:latest

## How to push image to your Docker Hub ?
-Login, create a repository(public/private)
docker tag node-mysql-image:v1.0.0 tuanflute275/node-mysql-image:v1.0.0

docker push tuanflute275/node-mysql-image:v1.0.0

Create container from your "custom image":


    docker run -dp 8002:8000 \
    --name node-mysql-container \
    -w /app -v "$(pwd):/app" \
    --network todo-app-network \
    -e MYSQL_HOST=todo-app-network-alias \
    -e MYSQL_USER=root \
    -e MYSQL_PASSWORD=Abc@123456789 \
    -e MYSQL_DB=todoDB \
    tuanflute275/node-mysql-image:v1.0.1 \
    sh -c "yarn install && yarn run:dev"

Update version:

    docker tag node-mysql-image:latest tuanflute275/node-mysql-image:v1.0.1
    docker push tuanflute275/node-mysql-image:v1.0.1

Create container with params/configurations

Put all params/configurations into a .yml file => Docker compose
docker-compose version

app services = multiple containers

Remove some containers:
docker rm -f netshoot-container
docker rm -f todo-app-container

docker rm -f node-mysql-container
docker rm -f mysql-container
docker network rm todo-app-network  

Start up the application stack:
-f : file
-d : detach(background mode)
docker-compose -f ./node-mysql-docker-composer.yml up -d 

Deploy your app to server => Kubenetes cluster
