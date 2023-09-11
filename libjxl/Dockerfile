FROM ubuntu:22.04

ENV DEBIAN_FRONTEND=noninteractive
RUN apt-get update && apt-get -y install tzdata
ENV TZ Asia/Tokyo
RUN apt-get update \
    && apt-get upgrade -y \
    && apt-get install -y \
    tzdata

# Install OpenImageIO
RUN apt-get update && apt-get -y install --no-install-recommends \
    build-essential \
    git \
    cmake \
    pkg-config \
    libbrotli-dev \
    libgif-dev \
    libjpeg-dev \
    libopenexr-dev \
    libpng-dev \
    libwebp-dev \
    clang \
    ca-certificates

RUN echo "export CC=clang" >> /etc/profile \
    && echo "export CXX=clang++" >> /etc/profile

RUN mkdir -p /root/local/src \
    && cd /root/local/src \
    && git clone https://github.com/libjxl/libjxl.git --recursive --shallow-submodules \
    && cd libjxl \
    && git submodule update --init --recursive --depth 1 --recommend-shallow \
    && mkdir build && cd build \
    && cmake -DCMAKE_BUILD_TYPE=Release -DBUILD_TESTING=OFF .. \
    && cmake --build . -- -j$(nproc) \
    && cmake --install .

# Added /etc/ld.so.conf
RUN echo "/usr/local/lib" >> /etc/ld.so.conf \
    && ldconfig

RUN mkdir -p /work/src

# Clean
RUN apt-get clean \
    && rm -rf /var/lib/apt/lists/* \
    && rm -rf /root/local/src
    