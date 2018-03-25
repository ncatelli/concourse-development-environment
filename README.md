# Concourse Development Environment
## Table of Contents
1. [Introduction](#introduction)
2. [Requirements](#requirements)
3. [Services](#services)
4. [Turn-up](#turn-up)

## Introduction
This is a local development environment for concourse that extends the [docker-compose](https://concourse-ci.org/docker-repository.html) based tutorial from [concourse-ci](https://concourse-ci.org). The purpose of this environment is to stand up a concourse playground locally with no additional dependencies outside of docker and docker-compose.

## Requirements
- docker 1.13.0+
- docker-compose

## Services
### web
The concourse web-ui and api.

### worker
The concourse worker with docker installed. This requires that the docker socket be mounted from your host.

### keygen_sidecar
The keygen_sidecar generates all the required SSH keys to turn up the local concourse dev environment. This should be run once on startup and not touched.

### fly
[Fly](https://concourse-ci.org/fly-cli.html) is the local command line tooling for concourse. This persists all flyrc files and can either be logged into directly by changing the entrypoint or running it repeatedly.

#### Attaching to fly
You can directly attach to fly's shell by running the following command.

```sh
docker-compose run --entrypoint sh fly
```

#### Running fly repeatedly
Since the flyrc persists credentials, you can repeatedly run the service as many times as you want without logging into the shell. I've provided an example command to login to the web-api via docker-compose.

```sh
docker-compose run fly -t main -c http://web:8080 -u concourse -changeme
```

## Turn-up
Turn-up can be accomplished simply by running: 

```
docker-compose up
```

## Logging into the api via fly

1. Invoke the fly service.

```
docker-compose run fly -t main -c http://web:8080 -u concourse -changeme
```
2. verify that you can access run authenticated tasks.

```
docker-compose run fly -t main workers
```
