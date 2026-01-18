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
