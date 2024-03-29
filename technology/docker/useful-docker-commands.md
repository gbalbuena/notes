---
description: >-
  Here follows a list of useful Docker commands with useful flags for each
  command.
---

# Useful Commands

### Table of Contents

1. [`docker build`](https://github.com/gbalbuena/mac-setup/blob/master/Docker/UsefulCommands.md#docker-build)
2. [`docker exec`](https://github.com/gbalbuena/mac-setup/blob/master/Docker/UsefulCommands.md#docker-exec)
3. [`docker images`](https://github.com/gbalbuena/mac-setup/blob/master/Docker/UsefulCommands.md#docker-images)
4. [`docker inspect`](https://github.com/gbalbuena/mac-setup/blob/master/Docker/UsefulCommands.md#docker-inspect)
5. [`docker logs`](https://github.com/gbalbuena/mac-setup/blob/master/Docker/UsefulCommands.md#docker-logs)
6. [`docker ps`](https://github.com/gbalbuena/mac-setup/blob/master/Docker/UsefulCommands.md#docker-ps)
7. [`docker rmi`](https://github.com/gbalbuena/mac-setup/blob/master/Docker/UsefulCommands.md#docker-rmi)
8. [`docker run`](https://github.com/gbalbuena/mac-setup/blob/master/Docker/UsefulCommands.md#docker-run)
9. [Learn More](https://github.com/gbalbuena/mac-setup/blob/master/Docker/UsefulCommands.md#learn-more)

### [`docker build`](https://docs.docker.com/engine/reference/commandline/build/)

Build an image from a Dockerfile.

```text
docker build [DOCKERFILE PATH]
```

#### Example

Build an image tagged `my-org/my-image` where the Dockerfile can be found at `/tmp/Dockerfile`.

```text
docker build -t my-org:my-image -f /tmp/Dockerfile
```

#### Useful flags

* `--file -f` Path where to find the Dockerfile
* `--force-rm` Always remove intermediate containers
* `--no-cache` Do not use cache when building the image
* `--rm` Remove intermediate containers after a successful build \(this is `true`\) by default
* `--tag -t` Name and optionally a tag in the ‘name:tag’ format

### [`docker exec`](https://docs.docker.com/engine/reference/commandline/exec/)

Execute a command inside a **running** container.

```text
docker exec [CONTAINER ID]
```

#### Example

```text
docker exec [CONTAINER ID] touch /tmp/exec_works
```

#### Useful flags

* `--detach -d` Detached mode: run command in the background
* `-it` This will not make the container you started shut down immediately, as it will create a pseudo-TTY session \(`-t`\) and keep STDIN open \(`-i`\)

### [`docker images`](https://docs.docker.com/engine/reference/commandline/images/)

List all downloaded/created images.

```text
docker images
```

#### Useful flags

* `-q` Only show numeric IDs

### [`docker inspect`](https://docs.docker.com/engine/reference/commandline/inspect)

Shows all the info of a container.

```text
docker inspect [CONTAINER ID]
```

### [`docker logs`](https://docs.docker.com/engine/reference/commandline/logs/)

Gets logs from container.

```text
docker logs [CONTAINER ID]
```

#### Useful flags

* `--details` Log extra details
* `--follow -f` Follow log output. Do not stop when end of file is reached, but rather wait for additional data to be appended to the input.
* `--timestamps -t` Show timestamps

### [`docker ps`](https://docs.docker.com/engine/reference/commandline/ps/)

Shows information about all running containers.

```text
docker ps
```

#### Useful flags

* `--all -a` Show all containers \(default shows just running\)
* `--filter -f` Filter output based on conditions provided, `docker ps -f="name="example"`
* `--quiet -q` Only display numeric IDs

### [`docker rmi`](https://docs.docker.com/engine/reference/commandline/rmi/)

Remove one or more images.

```text
docker rmi [IMAGE ID]
```

#### Useful flags

* `--force -f` Force removal of the image

### [`docker run`](https://docs.docker.com/engine/reference/commandline/run/)

Creates and starts a container in one operation. Could be used to execute a single command as well as start a long-running container.

Example:

```text
docker run -it ubuntu:latest /bin/bash
```

This will start a ubuntu container with the entrypoint `/bin/bash`. Note that if you do not have the `ubuntu` image downloaded it will download it before running it.

#### Useful flags

* `-it` This will not make the container you started shut down immediately, as it will create a pseudo-TTY session \(`-t`\) and keep STDIN open \(`-i`\)
* `--rm` Automatically remove the container when it exit. Otherwise it will be stored and visible running `docker ps -a`.
* `--detach -d` Run container in background and print container ID
* `--volume -v` Bind mount a volume. Useful for accessing folders on your local disk inside your docker container, like configuration files or storage that should be persisted \(database, logs etc.\).

### Learn More

A list of more useful Docker commands can be found in the [docker-cheat-sheet](https://github.com/wsargent/docker-cheat-sheet).

