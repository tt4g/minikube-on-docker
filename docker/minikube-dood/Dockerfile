ARG DDOCKER_VERSION=20.10.6

# https://hub.docker.com/_/docker
FROM docker:${DDOCKER_VERSION}

ARG KUBECTL_VERSION=v1.21.0
ARG MINIKUBE_VERSION=v1.19.0

    # Add build dependencies.
RUN apk --update --no-cache --virtual build-dependencies add \
    curl sudo \
    # Alpine Linux is not binary compatible with minikube, so add libc6-compat.
    # https://stackoverflow.com/a/57548061
    && apk --update --no-cache --virtual minikube-dependencies add \
    libc6-compat \
    # Install minikube.
    # https://minikube.sigs.k8s.io/docs/start/
    && curl -LO https://storage.googleapis.com/minikube/releases/${MINIKUBE_VERSION}/minikube-linux-amd64 \
    && sudo install minikube-linux-amd64 /usr/local/bin/minikube \
    && chmod +x /usr/local/bin/minikube \
    && rm minikube-linux-amd64 \
    # Install kubectl.
    # https://kubernetes.io/docs/tasks/tools/install-kubectl-linux/
    && curl -LO https://storage.googleapis.com/kubernetes-release/release/${KUBECTL_VERSION}/bin/linux/amd64/kubectl \
    && sudo install -o root -g root -m 0755 kubectl /usr/local/bin/kubectl \
    && rm kubectl \
    # Remove build dependencies.
    && apk del build-dependencies
