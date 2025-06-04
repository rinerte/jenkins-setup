1. docker inspect "socat container" // Look for IP
2. install plugin
3. Docker Host URI: tcp://IP:2375


# get id: getent group docker | cut -d: -f3
# build: docker build --build-arg DOCKER_GID={YOUR_HOST_GID} -t my-jenkins-agent .
# agent template settings
# Docker Image:my-jenkins-agent
# Pull strategy: never pull
# Mounts: type=bind,src=/var/run/docker.sock,dst=/var/run/docker.sock

set branch in pipeline
*/main