FROM nvidia/cuda:11.0.3-devel-ubuntu18.04

RUN apt-get update && apt-get install -y \
    apt-transport-https \
    autoconf \
    ca-certificates \
    git \
    gnupg \
    libc++-7-dev \
    libc++abi-7-dev \
    libglu1-mesa-dev \
    libosmesa6-dev \
    libsdl2-dev \
    libtbb-dev \
    libtool \
    libudev-dev \
    libxi-dev \
    ninja-build \
    python3-dev \
    software-properties-common \
    wget \
    xorg-dev \
 && rm -rf /var/lib/apt/lists/*

RUN wget -O - https://apt.kitware.com/keys/kitware-archive-latest.asc 2>/dev/null \
    | gpg --dearmor - | tee /etc/apt/trusted.gpg.d/kitware.gpg >/dev/null \
 && apt-add-repository --yes 'deb https://apt.kitware.com/ubuntu/ bionic main'

RUN apt-get update && apt-get install -y \
    cmake \
 && rm -rf /var/lib/apt/lists/*

RUN git clone https://github.com/ccache/ccache.git \
 && cd ccache \
 && git checkout v4.2 -b 4.2 \
 && mkdir build \
 && cd build \
 && cmake -DCMAKE_BUILD_TYPE=Release -DZSTD_FROM_INTERNET=ON .. \
 && make -j$(nproc) \
 && make install \
 && ccache --version \
 && ccache -M 10G

COPY . /root/Open3D

WORKDIR /root/Open3D
