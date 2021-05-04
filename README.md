# Overview

`minikube` with Docker on Docker.

## How to run

```bash
$ docker compose up -d --build
$ docker compose exec minikube-dood /bin/sh
```

## Use docker command to run

### Build image

```bash
$ docker image build -t minikube-dood:<VERSION> docker/minikube-dood/
```

### Run

```bash
$ docker run \
  -v /var/run/docker.sock:/var/run/docker.sock \
  -it \
  minikube-dood:<VERSION> \
  /bin/sh
```

## Start minikube

```bash
$ minikube start --force --driver=docker
```

NOTE: Must set `--force` option because Docker container run `root` user.
      See: https://github.com/kubernetes/minikube/issues/8257#issuecomment-689128598
