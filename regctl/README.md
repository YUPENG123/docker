https://hub.docker.com/r/regclient/regctl
regclient/regctl

#!/bin/sh
opts=""
case "$*" in
  "registry login"*) opts="-t";;
esac
docker container run $opts -i --rm --net host \
  -u "$(id -u):$(id -g)" -e HOME -v $HOME:$HOME \
  -v /etc/docker/certs.d:/etc/docker/certs.d:ro \
  ghcr.io/regclient/regctl:latest "$@"
