- It is used to create and manage multiple containers.
- We can specify port mapping, volume mapping and environment variable for each container

#### How to use docker compose
- Create a `docker-compose.yml` file.
- Write configurations inside it.
- run `run docker compose up`
- Docker will run all the containers specified in `Docker-compose.yml`
- `docker compose up -d` `=>` To run docker compose in background.
- To stop the containers `docker compose down`
- 
#### Example of `docker-compose.yml`
```yml
version: "3.8" # version of docker-compose

services: # list of services
  postgres: # service name can be anything
    image: postgres # base image name
    ports: # port mapping
      - "5432:5432"
    environment: # evironment variables
      POSTGRES_USER: postgres
      POSTGRES_DB: review
      POSTGRES_PASSWORD: password
    volumes: # list of volume mappings 
      - db-data:/var/lib/mysql
      - .:/app
    command: ./mvnw springboot:run #The command key in a Docker Compose file specifies the command that will be executed when the container is started. It will override cmd

  redis: 
    image: redis
    ports:
      - "6379:6379"
volumes: # We need to specify all the named volumes. for more details read volumes.
  db-data
```