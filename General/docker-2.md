


## Write your Dockerfile

### `FROM`
the base image to build on top of.
```
FROM [image:tag]
```

Usually the recommended distribution of a linux system to use a base is `Alpine`.
- `Alpine` is a minimal Docker image based on Alpine Linux with a complete package index and only 5 MB in size!


### `LABEL`
### `WORKDIR`

```
WORKDIR /path/to/workdir
```

The `WORKDIR` instruction sets the working directory for any `RUN`, `CMD`, `ENTRYPOINT`, `COPY` and `ADD` instructions that follow it in the Dockerfile. If the `WORKDIR` doesn’t exist, it will be created even if it’s not used in any subsequent Dockerfile instruction.

### `RUN`
### `CMD`
### `EXPOSE`
### `VOLUME`

```
VOLUME ["/data"]
```

Volumes are the preferred mechanism for persisting data generated by and used by Docker containers.


### `ENV`
### `ARG`
### `COPY`

```
COPY [--chown=<user>:<group>] <src>... <dest>
or
COPY [--chown=<user>:<group>] ["<src>",... "<dest>"]
```

The COPY instruction copies new files or directories from <src> and adds them to the filesystem of the container at the path <dest>.

### `ADD`
### `ENTRYPOINT`
```
ENTRYPOINT ["executable", "param1", "param2"]
```
You can use the exec form of `ENTRYPOINT` to set fairly stable default commands and arguments and then use either form of `CMD` to set additional defaults that are more likely to be changed.

















## Work with Docker Images

build an image from current working directory
```
docker build -t [username/reponame:tag] .
```

retag an image
```
docker image tag [image:tag(current)] [image:tag(new)]
```

push an image
```
docker login
docker push [image]
```

remove an image from local
```
docker image rm [image]
or
docker rmi [image]
```

remove multiple images
```
docker rmi [image] [image] [image]
```


list all dangling images
```
docker images -f dangling=true
```

remove all dangling images
```
docker image prune
```

remove multiple img







## Work with Docker Container

run a container
```
run [name]
```

Run bash shell in the interactive mode.
```
docker exec -it [Container Name] /bin/bash

e.g.
docker exec -it mystifying_thompson /bin/bash

```

list all containers
```
docker ps -a
```

list all exited containers

- `-a` for all
- `-f` for filter

```
docekr ps -a -f status=exited
```

remove all exited containers
- `-q` returns the ids of the containers

```
docker rm $(docker ps -a -f status=exited -q)
```


#### Purging All Unused or Dangling Images, Containers, Volumes, and Networks
- Docker provides a single command that will clean up any resources — images, containers, volumes, and networks — that are dangling (not associated with a container):
    ```
    docker system prune
    ```
- To additionally remove any stopped containers and all unused images (not just dangling images), add the -a flag to the command:
    ```
    docker system prune -a
    ```
