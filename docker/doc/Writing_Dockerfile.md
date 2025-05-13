To create your own custom Docker image, you need to write a Dockerfile – a plain text file with instructions Docker uses to build the image.
🛠 Basic Structure of a Dockerfile

Here's a simple example for a Java Spring Boot app:

# 1. Base image (use an official image with Java pre-installed)
FROM openjdk:17-jdk-slim

# 2. Set the working directory inside the container
WORKDIR /app

# 3. Copy the JAR file from the host into the container
COPY target/myapp.jar app.jar

# 4. Set the command to run the JAR
CMD ["java", "-jar", "app.jar"]

🔍 Step-by-Step Breakdown
Instruction	Description
FROM	Defines the base image (e.g., openjdk, ubuntu, node)
WORKDIR	Sets the working directory inside the container
COPY	Copies files from your project into the container
RUN	Executes commands during build (e.g., install packages)
CMD or ENTRYPOINT	Defines the default command to run when the container starts
🧪 Example: Dockerfile for a Node.js App

# Base image with Node.js
FROM node:20-alpine

# Set working directory
WORKDIR /usr/src/app

# Copy dependency files
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy app source code
COPY . .

# Expose the app port
EXPOSE 3000

# Start the app
CMD ["node", "index.js"]

🧱 Build the Image

docker build -t my-custom-image .

    The . at the end tells Docker to look for the Dockerfile in the current directory.

🚀 Run a Container from the Image

docker run -d -p 3000:3000 --name myapp my-custom-image

