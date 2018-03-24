# Dockerfile

You need to create a Dockerfile (with a Capital D) in the project's root directory for Docker to know how to build your
Docker Image.

## Creating a Dockerfile

Open the Dockerfile in your favorite text editor

The first thing we need to do is define from what image we want to build from. Here we will use the latest LTS (long term support) version carbon of node available from the Docker Hub:
```Docker
FROM node:carbon
```
Next we create a directory to hold the application code inside the image, this will be the working directory for your application:

Create app directory
```Docker
WORKDIR /usr/src/app
```
This image comes with Node.js and NPM already installed so the next thing we need to do is to install your app dependencies using the npm binary. Please note that if you are using npm version 4 or earlier a package-lock.json file will not be generated.

Install app dependencies
A wildcard is used to ensure both package.json AND package-lock.json are copied
where available (npm@5+)
```Docker
COPY package*.json ./
```

```Docker
RUN npm install
```
If you are building your code for production
RUN npm install --only=production
Note that, rather than copying the entire working directory, we are only copying the package.json file. This allows us to take advantage of cached Docker layers.

To bundle your app's source code inside the Docker image, use the COPY instruction:

Bundle app source
```Docker
COPY . .
```
Your app binds to port 8080 so you'll use the EXPOSE instruction to have it mapped by the docker daemon:
```Docker
EXPOSE 8080
```
Last but not least, define the command to run your app using CMD which defines your runtime. Here we will use the basic npm start which will run node server.js to start your server:
```Docker
CMD [ "npm", "start" ]
```

## A Node.js example for a Dockerfile
```Docker
FROM node:carbon
WORKDIR /usr/src/app
COPY package*.json ./
RUN npm install
COPY . .
EXPOSE 8080
CMD ["npm", "start"]
```
