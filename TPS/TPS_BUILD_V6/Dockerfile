FROM alpine:3.12 

RUN apk update && apk add --no-cache wget git curl bash

RUN apk add openjdk8

RUN git clone -b tps_docker https://github.com/ajshedivy/tps.git 