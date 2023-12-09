# How to build a docker image ?
**Step 1: Create a Dockerfile**\
The basic structure of dockerfile
```
  # Specify the base image
  FROM <base_image_name>

  # Install the dependecies
  RUN <installation_commad>

  # Specify the start-up command once creating a container from this image
  CMD ["startup","command"]
```
For example: to create a dockerfile for a nodejs application\n
```
  # Specify the base image is node:18-alpine in which nodejs is already installed
  FROM node:18-alpine

  # Specify the working directory so that all the afterwords commands will run from this directory
  WORKDIR /usr/app

  # Copy the package.json from local directory to base container created from base image and then installing all the dependencies listed in this json file
  COPY package.json ./
  RUN npm install

  # Copy the rest of source code from the local directory to temporary container
  COPY ./ ./

  # Specify the start-up command will start up the nodejs application
  CMD ["npm","start"]
```
**Step 2: Run build command**\
`docker build -t <docker_id>/<project_name>:<version>`
