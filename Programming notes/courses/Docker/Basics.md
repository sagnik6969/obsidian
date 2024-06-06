- `docker demon` `=>` It is actual backend of docker
- `docker desktop` `=>`  It is just a GUI to use features.
- `> docker` `=>` list of all available docker commands.
- `docker -v` `=>` Version 

- `docker run -it ubuntu` `=>` To run a docker image. `it` stands for interactive mode.
- It will also open a terminal inside the ubuntu.
- when we run the command it first checks if the image is present in the local machine if the image is present then it reuses it. Else it downloads it from [[hub.docker.com]]

### Container vs Image
A Docker container is a self-contained, runnable software application or service. On the other hand, a Docker image is the template loaded onto the container to run it, like a set of instructions. You store images for sharing and reuse, but you create and destroy containers over an application's lifecycle.

- Images are like Operating systems. 
- And container is like laptop. We need containers to run images.  Containers on their own is empty.
- We can run same image in multiple containers.
- Containers are isolated. Means 1 container cant access data of other container.

- When you are working on a project you will create a custom image.
- Example:  You can create a image containing `Ubuntu` `node` `monGodb` `redis`
- You have to publish the image in docker hub. And other developers will download it.
- 