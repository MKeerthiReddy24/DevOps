# 🚀 Day-1: Dockerize the Node.js Starter Project

This guide walks you through cloning a Node.js starter project, creating a Docker image, pushing it to Docker Hub, and running it in any environment.
### 1. Clone the Git hub Repository in the server
``` bash
git clone <github-url>
```
### 2.cd into the directory
``` bash
  cd <folder-name>
```
### 3. Create a docker file
``` bash
touch Dockerfile
```
### 4. Paste the below content into the docker file
``` bash
FROM node:18-alpine
WORKDIR /app
COPY package.json ./
RUN yarn install --production
COPY . .
EXPOSE 3000
CMD ["node", "index.js"]
```
### 5. Samewise create package.json and index.js files
###### index.js
``` bash
const express = require("express");
const app = express();

app.get("/", (req, res) => {
  res.send("Server running successfully!");
});

app.listen(3000, () => {
  console.log("Server is running on port 3000");
});
```

###### package.json
``` bash
{
  "name": "first-image-node",
  "version": "1.0.0",
  "main": "index.js",
  "dependencies": {
    "express": "^4.18.2"
  }
}
```
### 6. Build the docker image using the application code and Dockerfile
``` bash
docker build -t <image-name> .
### 7. Verify the image has been created and stored locally using the below command:
``` bash
docker images
```
### 8. Create a public repository on hub.docker.com and push the image to remote repo
``` bash
docker tag <local-image>:tag username/<image/repo-to-be-pushed>:tag
docker images
docker push username/<image/repo-to-be-pushed>:tag
```
### 9. To pull the image to another environment , you can use below command
``` bash
docker pull username/<image/repo-to-be-pushed>:tag
```
### 10. To start the docker container, use below command
``` bash
docker run -dp 3000:3000 username/<image/repo-to-be-pushed>:tag
```
### 11. To check the containers
``` bash
docker ps
```
### 12. To check the container status
``` bash
docker ps -a
```
### 13. To check the container logs
``` bash
docker logs <container_id>
```

#### Verify your app. If you have followed the above steps correctly, your app should be listening on localhost:3000

#### To enter(exec) into the container, use the below command
``` bash
docker exec -it containername sh
or
docker exec -it containerid sh
```


#### Working of Docker file

FROM node:18-alpine : This is the base image where it contains all nodejs installed  and  yarn, npm available. alpine is a small OS.
WORKDIR /app : Docker creates a folder /app inside the container. All future commands (COPY, RUN, CMD) run inside this folder automatically.
COPY package.json yarn.lock ./ : only copy the package.json and yarn.lock files into the working directory i.e /app. This represents node dependencies.
RUN yarn install --production : Inside the container, Docker runs
``` bash
yarn install --production
```
Yarn creates a node_modules folder inside the container.
Only "dependencies" (not devDependencies) are installed.
This creates a new image layer.

COPY . . : Copies all files in your project folder into /app.
EXPOSE 3000 : Documents that your container uses port 3000. It does NOT publish the port.
CMD ["node", "index.js"] : This defines the default command that runs when the container starts.
Docker runs:
``` bash
node index.js
```
#### 🚀 What happens when you run the container?
##### When you run:
``` bash
docker run -dp 3000:3000 first-image-node
```
Docker does:
##### Step 1: Start the container
Loads the built image and creates a new container from it.
##### Step 2: Map ports
Host 3000 → Container 3000
##### Step 3: Execute CMD
Runs:
``` bash
node index.js
```
##### Step 4: Node server starts
Your Node Express app listens at:
``` bash
localhost:3000
```
##### If CMD exits → container stops.
