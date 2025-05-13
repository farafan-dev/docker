🏗️ Building Custom Docker Images – Complete Guide

Building custom Docker images means packaging your application and its dependencies into a reusable, portable, and versioned container image.
🔹 Step 1: Create a Dockerfile

The Dockerfile is a set of instructions Docker reads to build the image.
🔸 Example 1 – Java Spring Boot App

# Use base image with Java runtime
FROM openjdk:17-jdk-slim

# Set working directory
WORKDIR /app

# Copy JAR file into image
COPY target/myapp.jar app.jar

# Define default command
CMD ["java", "-jar", "app.jar"]

🔸 Example 2 – Python App

FROM python:3.11-slim

WORKDIR /app

COPY requirements.txt .

RUN pip install -r requirements.txt

COPY . .

CMD ["python", "app.py"]

🔸 Example 3 – Node.js App

FROM node:20-alpine

WORKDIR /usr/src/app

COPY package*.json ./

RUN npm install

COPY . .

EXPOSE 3000

CMD ["node", "index.js"]

🔹 Step 2: Build the Docker Image

Use the docker build command:

docker build -t <image_name>:<tag> .
# Example:
docker build -t myapp:1.0 .

🔹 Step 3: Run the Docker Image as a Container

docker run -d -p 8080:8080 --name mycontainer myapp:1.0

🔹 Step 4: Verify Everything
🔸 Check if the container is running

docker ps

🔸 View logs

docker logs mycontainer

🔹 Optional Enhancements
🧊 Use .dockerignore

Like .gitignore, exclude files from build context:

node_modules
target
*.log
.env

🧪 Multi-stage builds (e.g., for Java)

Build in one stage, run in another to reduce image size:

# Stage 1: Build
FROM maven:3.9-openjdk-17 AS builder
WORKDIR /build
COPY . .
RUN mvn clean package

# Stage 2: Run
FROM openjdk:17-jdk-slim
WORKDIR /app
COPY --from=builder /build/target/myapp.jar app.jar
CMD ["java", "-jar", "app.jar"]

📌 Summary
Command	Description
docker build -t myapp:1.0 .	Build image
docker images	List images
docker run -d -p 8080:8080 myapp:1.0	Run container
docker ps	List running containers
docker logs mycontainer	View logs

Let me know your tech stack or project type and I’ll give you a ready-to-use Dockerfile and build commands 