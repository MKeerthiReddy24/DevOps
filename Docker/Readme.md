# Day-1 Dockerize the node starter project
1. Clone the Git hub Repository in the server
``` bash
git clone <github-url>
```
2.cd into the directory
``` bash
  cd <folder-name>
```
3. Create a docker file
``` bash
touch Dockerfile
```
4. Paste the below content into the docker file
``` bash
FROM node:18-alpine
WORKDIR /app
COPY package.json ./
RUN yarn install --production
COPY . .
EXPOSE 3000
CMD ["node", "index.js"]
```
5. Samewise create package.json and index.js files
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
