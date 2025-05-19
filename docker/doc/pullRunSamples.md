### docker images

### docker image pull redis

### docker container run redis

### docker container run -P httpd


    docker container run: This command is used to create and start a new container from a specified image.
    -P (uppercase P): This option tells Docker to publish all exposed ports from the container to random ports on the host machine.
    httpd: This is the image name, in this case the Apache HTTP Server image (official image from Docker Hub).
**************
to find port
### dministrator@srv4605952752:/mnt/c/Users/Administrator$ docker container ls
    CONTAINER ID   IMAGE     COMMAND              CREATED         STATUS         PORTS                                       NAMES
    f3d250880e1b   httpd     "httpd-foreground"   9 minutes ago   Up 9 minutes   0.0.0.0:32768->80/tcp, [::]:32768->80/tcp   adoring_dijkstra


check  http://localhost:32768/


***********

docker container create -p 80:80 httpd

docker container ls


    CONTAINER ID   IMAGE     COMMAND              CREATED          STATUS          PORTS                                       NAMES
    f3d250880e1b   httpd     "httpd-foreground"   19 minutes ago   Up 19 minutes   0.0.0.0:32768->80/tcp, [::]:32768->80/tcp   adoring_dijkstra

docker container start f3d250880e1b

docker container ls -a

check  http://localhost


*********

docker container run -d -p 8080:80 --name mysite nginx

    dministrator@srv4605952752:/mnt/c/Users/Administrator$ docker container run -d -p 8080:80 --name mysite nginx
    933c0ea4e3fe5ca90f6b3fe0a35d697ef239b1972e77b02cc51ceb6661e22ba8

🔧 Command Breakdown:

    docker container run: Runs a new container from a specified image.

    -d: Runs the container in detached mode (in the background).

    -p 8080:80: Maps port 80 of the container (which is the default port used by nginx) to port 8080 on the host.
    So you can access the Nginx server at http://localhost:8080.

    --name mysite: Assigns a custom name (mysite) to the container.
    This makes it easier to manage later using commands like docker stop mysite.

    nginx: Specifies the Docker image to use. In this case, it's the official Nginx web server image from Docker Hub.

🧠 What This Command Does:

    Pulls the nginx image (if not already present).

    Creates a container named mysite.

    Runs it in the background.

    Maps the container’s port 80 to your host’s port 8080.

    Starts the Nginx web server inside the container.

📍 Test It:

Open your browser and go to:

http://localhost:8080


************

docker container create redis

docker container start 64624675a395cd34389fd88d14f6ccd7a2c231fb5244c3a7bde48dc35c99a4e5 && ping 127.0.0.1
docker ps
docker container ls -a -f status=exited
docker container ls -a -f status=exited -q
****************

docker container run -d -P --name mywebsite nginx

docker container ls

docker container stop

docker container rm 

docker container rm -f

docker container ls -a -f status=exited -q

**************************
docker container rm $(docker container ls -a -f status-exited -q

docker container rm $(docker container ls -a -f status=exited -q) 2>/dev/null || echo "No exited containers to remove."
****************

docker image rm centos
docker image rm -f centos

*********
docker container run --name=container1 centos:7

docker container run --name=container2 centos:7 cat /etc/passwd

docker container run --name=container3 -it centos:7


        Ctrl + P + Q

docker container exec -it d4 bash

docker container stop container3
********************
docker container run -d -p 8080:80 --name=mysite nihnx
 





