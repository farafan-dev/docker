🐳 Build an image

docker build -t <image_name>:<tag> .
# Example:
docker build -t myapp:latest .

🐳 Run a container

docker run [OPTIONS] <image_name>
# Example:
docker run -d -p 8080:80 --name mycontainer myapp:latest

🐳 List images

docker images

🐳 List running containers

docker ps

🐳 List all containers (including stopped)

docker ps -a

🐳 Stop a container

docker stop <container_id_or_name>

🐳 Remove a container

docker rm <container_id_or_name>

🐳 Remove an image

docker rmi <image_id_or_name>

🔹 Working with Containers
🐳 Execute a command in a running container

docker exec -it <container_id_or_name> <command>
# Example:
docker exec -it mycontainer bash

🐳 Start an interactive shell inside a container

docker exec -it <container_name> /bin/bash
# or if bash is not available:
docker exec -it <container_name> /bin/sh

🐳 Copy files between host and container

docker cp <container_id>:/path/in/container /path/on/host
docker cp /path/on/host <container_id>:/path/in/container

🔹 Volumes & Logs
🐳 View container logs

docker logs <container_id_or_name>

🐳 Mount a volume

docker run -v /host/path:/container/path <image>

🔹 Networking
🐳 List networks

docker network ls

🐳 Create a network

docker network create <network_name>

🐳 Connect a container to a network

docker network connect <network_name> <container_name>

🔹 Cleanup Commands
🐳 Remove all stopped containers

docker container prune

🐳 Remove unused images

docker image prune

🐳 Remove all unused data (containers, images, volumes, networks)

docker system prune

