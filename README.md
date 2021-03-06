# Docker in Docker

This repository contains tools to generate Docker in Docker images.

## Repository Organization

For every version of Docker, there is a corresponding git tag in this repository containing a `Dockerfile`
able to build a Docker-in-Docker image of that version.

Example:
```
$ git co v1.0.0
$ docker build -t dind .
$ docker run --privileged dind docker version
Client version: 1.0.0
```

Every version is built and pushed to the [Docker Hub](https://hub.docker.com/u/dockerswarm/dind):

```
$ docker run --rm --privileged -it dockerswarm/dind:1.0.0 docker version
Client version: 1.0.0
```

## Tools

### update.sh

For every tag in `docker/docker` that is not present in this repository, create a corresponding tag with an updated
`Dockerfile`.

## build_and_push.sh

Build and push the given Docker images. If not arguments are given, it will build and push **all** images.
