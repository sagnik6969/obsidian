- Note in images like node an OS like ubuntu is installed in which `nodejs` is preinstalled.
- When we run  `nodejs` image it directly runs node instead of opening a bash shell. because that is specified as entry point of that image. 

#### What is dockerizing An Application ?
- Dockerizing means creating a docker image for the application.
- The image will contain everything required to run that application (OS, Application code, Compiler etc).
- This helps to streamline the deployment process.
- While deploying the app we just need to pull the docker image and run it (No need for environment setup).
- 
#### How to dockerize an app
- We need to create a `Dockerfile` in the root of the app.
- In this file we write all the configurations on how to create the docker image.
- Then run `docker build -t <image name>`
- To run the generated image `docker run it <imagename>`
- 
#### Example of `Dockerfile`

```Dockerfile
FROM ubuntu

RUN apt-get update
RUN apt-get install -y curl
RUN curl -sL https://deb.nodesource.com/setup_18.x | bash -
RUN apt-get upgrade -y
RUN apt-get install -y nodejs

COPY package.json package.json
COPY package-lock.json package-lock.json
RUN npm install

COPY main.js main.js



ENTRYPOINT [ "node", "main.js" ]
```
#### `Dockerfile` commands
- `FROM` `=>` Used to specify a base image
- `RUN` `=>` Used to run a specific command
- `CMD` `=>` Specifies a command that need to be executed when a docker container starts.
- `ENTRYPOINT` `=>` Used to set executables which will always run when the container is initiated. Unlike CMD command, this cant be overridden.
- `WORKDIR` `=>` To specify a working directory inside the container.
- `COPY` `=>` to copy file for folder from your local machine to docker container.
- `ADD` `=>` Similar to `COPY`. It also allows you to copy data from URL or a tar file. 
- `EXPOSE` `=>` Specifies that the container is listening to a specific port in the network.
- `LABEL` `=>` To add metadata to a docker image. It is a key value pair.
- `VOLUME` `=>` To mount a volume to docker container from the host file system.
- `ENV` used to set environment variables with key and value.


#### Cashing 
- Lines In a `dockerfile` are cashed.
- When rebuilding an image if a line needs to rerun. Then all the subsequent lines need to be rerun.
- That's why in the above example we have run `npm install` before copying `main.js`.
- When `main.js` changes it will not rerun `npm install`.
- 
- 

https://www.youtube.com/watch?v=vm3YfOHf_Cc
