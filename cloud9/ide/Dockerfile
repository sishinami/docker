FROM ubuntu:16.04
LABEL maintainer "sysopjp"

RUN apt-get update -y \
    && apt-get install -y nodejs npm curl git sudo \
    && apt-get clean \
    && rm -fr /var/lib/apt/lists/*

RUN npm cache clean \
    && npm install n -g

RUN n 0.12.18 \
    && ln -sf /usr/local/bin/node /usr/bin/node \
    && apt-get purge -y nodejs npm

# create docker user
RUN useradd -d /home/docker -m -s /bin/bash -u 1000 -g 50 docker

USER 1000
RUN git clone https://github.com/c9/core.git /home/docker/cloud9 \
    && cd /home/docker/cloud9 \
    && ./scripts/install-sdk.sh

USER root
RUN mkdir -p /workspace
VOLUME ["/workspace"]
WORKDIR /workspace

USER 1000
