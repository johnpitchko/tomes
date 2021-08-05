# Docker

## Building an image from a Dockerfile

```
$ docker build .
```

This assumes your build file is called `Dockerfile`. If its called anything else you can specify with the `-f` flag:

```
$ docker build -f <build file name> .
```

## Prune images

Prune all images _not_ associated with a container:

```
docker image prune -a
```

# Docker Compose

## Build the image

```
$ docker compose build
```

## Launch images and services with Docker Compose

```
$ docker compose up -d
```

`-d` will run the containers in the background.

## Prune containers

```
docker container prune
```

## View logs

```
$ docker-compose logs
```

## View active/running containers

```
docker ps
```

## Execute commands within an active container

`<continer name>` can be found using the `docker ps` command.

```
docker exec <container name> <command>
```

## Connect to the container's terminal/shell

```
docker exec -it <container name> /bin/sh
```

You can replace `/bin/sh` with `/bin/bash` (or whichever shell program you like), however not every container image contains `bash`. On the other hand *every* distro will at least include the basic `sh` shell.

# Docker for Rails

Below is information specific for using Docker with Rails applications.

## Open a Rails console within a running container

```bash
$ docker exec -it <container name> rails c
```
Source [EquiValent](https://blog.eq8.eu/til/how-to-lunch-rails-console-in-specific-docker-container.html)

# Best Practices

Source: [Best Practices Around Production Ready Web Apps with Docker Compose](https://nickjanetakis.com/blog/best-practices-around-production-ready-web-apps-with-docker-compose)

## Docker Compose

1. Do not add a `version` property at the top of the file.
2. Define healthchecks in `docker-compose.yml` rather than `Dockerfile`.
