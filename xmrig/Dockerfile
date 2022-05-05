FROM nvidia/cuda:10.0-cudnn7-runtime-ubuntu18.04
LABEL maintainer="obikata <https://github.com/obikata>"

RUN apt-key adv --keyserver keyserver.ubuntu.com --recv-keys A4B469963BF863CC

RUN apt-get update

# Install prerequisites
RUN apt-get install -y \
        vim \
        wget \
        git

# Install sudo
RUN apt-get install -y sudo

# Add sudo user
RUN groupadd -g 1000 obikata && \
    useradd  -g      obikata -G sudo -m -s /bin/bash obikata && \
    echo 'obikata:nopasswd' | chpasswd

RUN echo 'Defaults visiblepw'             >> /etc/sudoers
RUN echo 'obikata ALL=(ALL) NOPASSWD:ALL' >> /etc/sudoers

# Remove package list
RUN rm -rf /var/lib/apt/lists/*

# Set default user
USER obikata

# Reset workdir
WORKDIR /home/obikata
