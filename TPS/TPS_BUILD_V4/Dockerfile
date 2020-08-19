FROM ubuntu:20.04

ENV DEBIAN_FRONTEND=noninteractive
# CHANGE USER
USER root

# INSTALL JAVA
RUN apt-get update && apt-get -y install default-jdk git curl

# Set JAVA_HOME From sudo update-alternatives --config java
RUN echo '/usr/lib/jvm/java-8-openjdk-amd64/jre/bin/java' >> /etc/environment

# install TPS
WORKDIR /home/TPS_HOME
RUN git clone -b tps_docker https://github.com/ajshedivy/tps.git

