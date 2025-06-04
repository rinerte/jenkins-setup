FROM jenkins/inbound-agent:latest
USER root

# Get host's Docker group GID during build
ARG DOCKER_GID
RUN if [ -z "$DOCKER_GID" ]; then groupadd docker; else groupadd -g $DOCKER_GID docker; fi
RUN usermod -aG docker jenkins

RUN apt-get update && apt-get install -y docker.io
USER jenkins
ENV DOCKER_HOST=unix:///var/run/docker.sock

# get id: getent group docker | cut -d: -f3
# build: docker build --build-arg DOCKER_GID={YOUR_HOST_GID} -t my-jenkins-agent .
# agent template settings
# Docker Image:my-jenkins-agent
# Pull strategy: never pull
# Mounts: type=bind,src=/var/run/docker.sock,dst=/var/run/docker.sock