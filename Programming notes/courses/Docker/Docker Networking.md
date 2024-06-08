#### Bridge
- Default network driver in a docker container in `Bridge`
- It creates a bridge between a host machine and container so that container can talk to the internet.

#### Host
- To use host driver for networking `docker run -it network=host <img_name>`
- Here the container is directly connected to host machine.
- No need for port mapping.
- We can automatically acc4ss the ports.
#### NONE
- To use none driver for networking `docker run -it network=none <img_name>`
- Here docker wont use any network driver.
- The container will be disconnected from the internet.
#### To create a custom network
- `docker network create -d bridge <network_name>`
- here `beidge` is default driver.
- When two containers are connected to the same network they can talk to each other.
- to connect a container to a network `docker run -it network=<network_name> <img_name>`
- To ping a container from terminal of another container. `ping <another_container_name>`
#### To list all the available networks
- `docker network ls`
- 