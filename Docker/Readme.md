# Day-1 Dockerize the node starter project
1. Clone the Git hub Repository in the server
``` bash
git clone <github-url>
```
2. cd into the directory
``` bash
  cd <folder-name>
```
3. Create a docker file
``` bash
touch Dockerfile
```
4. paste the below content into the docker file
``` bash
FROM node:18-alpine
WORKDIR /app
COPY package.json ./
RUN yarn install --production
COPY . .
EXPOSE 3000
CMD ["node", "index.js"]
```
   
