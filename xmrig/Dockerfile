FROM nvidia/cuda:10.1-cudnn7-devel-ubuntu18.04
LABEL maintainer="obikata <https://github.com/obikata>"

RUN apt-key adv --keyserver keyserver.ubuntu.com --recv-keys A4B469963BF863CC

RUN apt-get update

# Install prerequisites
RUN apt-get install -y \
        vim \
        wget \
        git

# Install dependencies for xmrig and xmrig-cuda
RUN apt-get install git build-essential cmake libuv1-dev libssl-dev libhwloc-dev -y
RUN apt-get install git automake libtool autoconf -y

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

# Install xmrig
RUN git clone https://github.com/xmrig/xmrig.git
RUN mkdir xmrig/build
WORKDIR /home/obikata/xmrig/scripts
RUN ./build_deps.sh
WORKDIR /home/obikata/xmrig/build
RUN cmake .. -DXMRIG_DEPS=scripts/deps
RUN make -j$(nproc)

# Reset workdir
WORKDIR /home/obikata

# Install xmrig-cuda
RUN git clone https://github.com/xmrig/xmrig-cuda.git
RUN mkdir xmrig-cuda/build 
WORKDIR /home/obikata/xmrig-cuda/build
RUN cmake .. -DCUDA_LIB=/usr/local/cuda/lib64/stubs/libcuda.so -DCUDA_TOOLKIT_ROOT_DIR=/usr/local/cuda
RUN make -j$(nproc)

# Reset workdir
WORKDIR /home/obikata
