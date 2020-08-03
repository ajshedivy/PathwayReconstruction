FROM ubuntu:20.04

# PARAMETERS
ENV CYTOSCAPE_VERSION 3.8.0
ENV DEBIAN_FRONTEND=noninteractive

# CHANGE USER
USER root

# INSTALL JAVA
RUN apt-get update && apt-get -y install default-jdk libxcursor1 xvfb supervisor wget x11vnc git vim 
RUN wget --progress=dot:giga --local-encoding=UTF-8 -v https://github.com/cytoscape/cytoscape/releases/download/3.8.0/cytoscape-unix-3.8.0.tar.gz -O cytoscape-unix-3.8.0.tar.gz
RUN tar xf cytoscape-unix-3.8.0.tar.gz && rm cytoscape-unix-3.8.0.tar.gz

RUN mkdir /home/TPS_HOME
WORKDIR /home/TPS_HOME
RUN wget https://repo.anaconda.com/miniconda/Miniconda2-latest-Linux-x86_64.sh -O ~/miniconda.sh && \
    /bin/bash ~/miniconda.sh -b -p /opt/conda && \
    rm ~/miniconda.sh && \
    /opt/conda/bin/conda clean --all && \
    ln -s /opt/conda/etc/profile.d/conda.sh /etc/profile.d/conda.sh && \
    echo ". /opt/conda/etc/profile.d/conda.sh" >> ~/.bashrc && \
    echo "conda activate base" >> ~/.bashrc

# install TPS
WORKDIR /home/TPS_HOME
RUN git clone -b tps_docker https://github.com/ajshedivy/tps.git

# Set JAVA_HOME From sudo update-alternatives --config java
RUN echo 'JAVA_HOME="/usr/lib/jvm/java-11-openjdk-amd64"' >> /etc/environment

COPY supervisor/supervisord.conf /etc/supervisor/conf.d/supervisord.conf

EXPOSE 1234 5900
CMD ["/usr/bin/supervisord"]
