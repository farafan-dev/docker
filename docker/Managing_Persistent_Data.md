🔹 1. Docker Network (Manual Method)

By default, Docker creates a bridge network. But for inter-container communication, it’s better to create a custom network:
➤ Step-by-step:

# Create a custom bridge network
docker network create my-network

# Run containers attached to that network
docker run -d --name backend --network my-network backend-image
docker run -d --name frontend --network my-network frontend-image

    Now, frontend can reach backend using the name backend as the hostname.

🔹 2. Docker Compose (Recommended for Multiple Containers)

Docker Compose makes it easier to define and connect multiple services:
➤ docker-compose.yml

version: "3.9"
services:
backend:
image: backend-image
ports:
- "8080:8080"

frontend:
image: frontend-image
ports:
- "3000:3000"
depends_on:
- backend

    All services are automatically in the same network.

    You can reach backend from frontend using http://backend:8080.

🔹 3. Docker Swarm (for production-scale orchestration)

In Swarm mode, Docker manages an overlay network across multiple nodes.

docker swarm init

docker network create \
--driver overlay \
--attachable \
swarm-net

docker service create --name backend --network swarm-net backend-image
docker service create --name frontend --network swarm-net frontend-image

🔹 4. Kubernetes (Advanced, Cloud-native)

In Kubernetes, Pods can communicate over a flat network using services and DNS.
### 🔸 Summary Table

| Method           | Networking Type     | Container Discovery       | Suitable For              |
|------------------|---------------------|---------------------------|---------------------------|
| Docker CLI       | Custom bridge       | Container name            | Small setups / dev        |
| Docker Compose   | User-defined bridge | Service name in compose   | Local dev / small projects|
| Docker Swarm     | Overlay             | Service name              | Production / clusters     |
| Kubernetes       | ClusterIP + DNS     | Service name via DNS      | Large-scale / cloud-native|
