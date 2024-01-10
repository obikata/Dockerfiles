FROM ubuntu:22.04
LABEL maintainer="obikata <https://github.com/obikata>"

RUN apt-get update

# Install prerequisites
RUN apt-get install -y \
        vim \
        wget \
        git

# Install prerequisites for OpenCV
RUN apt-get install -y libgl1 libgtk2.0-dev

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

# Install anaconda
WORKDIR /home/obikata/tmp
RUN set -x && \ 
    wget https://repo.anaconda.com/archive/Anaconda3-2023.09-0-Linux-x86_64.sh && \
    bash Anaconda3-2023.09-0-Linux-x86_64.sh -b && \
    rm Anaconda3-2023.09-0-Linux-x86_64.sh

# Reset workdir
WORKDIR /home/obikata

# Run conda init
RUN anaconda3/bin/conda init
