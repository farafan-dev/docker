Docker Compose is a tool used to define and manage multi-container Docker applications. With it, you can describe an entire stack (services, networks, volumes, etc.) in a single docker-compose.yml file, and then easily run and manage everything with a single command.
📦 Example docker-compose.yml

version: '3.8'

services:
web:
image: nginx:latest
ports:
- "8080:80"
volumes:
- ./html:/usr/share/nginx/html:ro

app:
build: ./app
depends_on:
- db
environment:
- DATABASE_URL=postgres://user:password@db:5432/mydb

db:
image: postgres:14
environment:
POSTGRES_USER: user
POSTGRES_PASSWORD: password
POSTGRES_DB: mydb
volumes:
- db_data:/var/lib/postgresql/data

volumes:
db_data:

🛠 Common Commands
Command	Description
docker-compose up	Start all services (add -d to run in background)
docker-compose down	Stop and remove containers, networks, etc.
docker-compose build	Build images from Dockerfiles
docker-compose logs	View logs for all services
docker-compose ps	List running containers
docker-compose exec SERVICE bash	Open a terminal in a running service
✅ Benefits

    Manage multi-container setups with ease.

    Define infrastructure as code.

    Useful for both development and testing environments.

    Easy to scale and extend (e.g. add Redis, Elasticsearch, etc.).