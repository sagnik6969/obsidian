- Volumes are used for data persistence in docker.
- Containers use a virtual file system. If we delete a container or restart a container then data in the virtual file system is gone and it starts from a fresh state.
#### What is docker volumes
- A directory in hist file system is mounted to a directory inside docker container.
- When container writes into the file system it automatically gets replicated to the host machine mounted directory.
- And If we change something in the host file system it automatically gets replicated inside the container.

#### Different ways to create a docker volume
- `docker run -v host_dir:container_dir img_name`
- `docker rum -v container_dir img_name` `=>` docker will automatically create an anonymous volume and map it to `container_dir` 
- `docker rum -v name:container_dir img_name` `->` Named volumes. Give name to anonymous volume so that it can be referenced later.

#### Names Volumes inside docker compose
```yml

services:
  db:
    image: mariadb:10.6.4-focal
    volumes:
      - db-data:/var/lib/mysql

volumes:
  db-data
```
- At last we need to reference all the named volumes in `volumes:` This lets us to reuse named volumes in different containers.
- If we don't use named volumes then we don't need to reference them at last.
- 