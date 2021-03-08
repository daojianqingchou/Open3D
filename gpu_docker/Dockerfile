FROM nvidia/cuda:11.0.3-devel-ubuntu18.04

RUN apt-get update && apt-get install -y \
    apt-transport-https \
    ca-certificates \
    gnupg \
    software-properties-common \
    wget \
 && rm -rf /var/lib/apt/lists/*

RUN wget -O - https://apt.kitware.com/keys/kitware-archive-latest.asc 2>/dev/null \
    | gpg --dearmor - | tee /etc/apt/trusted.gpg.d/kitware.gpg >/dev/null \
 && apt-add-repository --yes 'deb https://apt.kitware.com/ubuntu/ bionic main'

RUN apt-get update && apt-get install -y \
    cmake \
    xorg-dev \
    libglu1-mesa-dev \
    python3-dev \
 && rm -rf /var/lib/apt/lists/*
