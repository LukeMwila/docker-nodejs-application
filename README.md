# Dockerized Node.js Backend Application
This repository contains source code for a basic `to-do` CRUD (Create, Read, Update, Delete) based Node.js application. The application source code also contains a `Dockerfile` to build an image and containerize the application.

## Folder Structure
```
├── Dockerfile
├── README.md
├── package-lock.json
├── package.json
└── src
   ├── app.js
   ├── config
   ├── controllers
   ├── index.js
   ├── models
   ├── routes
   └── test
```

## Dockerfile
```
FROM node:14-alpine
WORKDIR /usr/src/app
COPY ["package.json", "package-lock.json*", "npm-shrinkwrap.json*", "./"]
RUN npm install 
COPY . .
EXPOSE 3001
RUN chown -R node /usr/src/app
USER node
CMD ["npm", "start"]
```

## Run Application with Docker
Run the following commands in your terminal to build the image, start a container and test the application.
```
docker build -t <image-tag> .
docker run -p 3001:3001 <image-tag>
curl http://127.0.0.1:3001
```