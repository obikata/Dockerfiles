FROM ubuntu:18.04
LABEL maintainer="obikata <https://github.com/obikata>"

# apt update
RUN apt-get update

# install dependencies for petalinux
RUN dpkg --add-architecture i386
RUN apt-get update
RUN apt-get install apt-utils libc6:i386 libncurses5:i386 libstdc++6:i386 g++-multilib libgtk2.0-0:i386 dpkg-dev:i386 libxtst6:i386 default-jre unzip net-tools libtext-csv-perl libcanberra-gtk-module libcanberra-gtk3-module lsb-core opencl-headers ocl-icd-opencl-dev ocl-icd-libopencl1 wget tofrodos iproute2 gawk make locales cpio libncurses5-dev libssl-dev flex bison libselinux1 gnupg diffstat chrpath socat xterm autoconf libtool libtool-bin tar texinfo zlib1g-dev gcc-multilib build-essential libsdl1.2-dev libglib2.0-dev screen pax gzip xvfb tftpd tftp lsb-release zlib1g:i386 git python-dev xxd -y
RUN locale-gen en_US.UTF-8
RUN ln -s /usr/bin/make /usr/bin/gmake

RUN apt-get upgrade -y

# install sudo
RUN apt-get install -y sudo

# add sudo user
RUN groupadd -g 1000 obikata && \
    useradd  -g      obikata -G sudo -m -s /bin/bash obikata && \
    echo 'obikata:nopasswd' | chpasswd

RUN echo 'Defaults visiblepw'             >> /etc/sudoers
RUN echo 'obikata ALL=(ALL) NOPASSWD:ALL' >> /etc/sudoers

# remove package list
RUN rm -rf /var/lib/apt/lists/*

# Reset workdir
WORKDIR /home/obikata

USER obikata

