FROM ubuntu:latest

LABEL maintainer="nathan.levy.au@gmail.com"

RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
    && apt-get -y install --no-install-recommends build-essential

ENTRYPOINT ["/bin/bash"]
