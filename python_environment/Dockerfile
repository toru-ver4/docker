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
    ninja-build \
    yasm \
    cmake \
    nasm \
    cbindgen \
    cargo \
    libxml2-dev \
    pkg-config \
    libtiff5-dev \
    libboost-all-dev \
    libpng-dev \
    libopenexr-dev \
    libraw-dev \
    libheif-dev \
    ffmpeg \
    libopenjp2-7-dev \
    curl \
    unzip \
    libssl-dev \
    gpac \
    doxygen \
    libilmbase-dev \
    libxcomposite-dev \
    libxkbcommon-x11-dev \
    mesa-common-dev \
    imagemagick \
    python3-pip \
    python3-pybind11 \
    python3-setuptools \
    python3-wheel \
    python3-tk \
    libwebp-dev \
    qt5dxcb-plugin \
    libxcb-icccm4 \
    libxcb-image0-dev \
    libxcb-keysyms1-dev \
    libxcb-randr0-dev \
    libxcb-render-util0-dev \
    libxcb-xinerama0-dev \
    libgtest-dev

# Install Basic Python Libraries
RUN apt-get update && apt-get -y install \
    python3-venv \
    libsm-dev \
    libxrender-dev \
    python3-tk
RUN mkdir /work && cd /work \
    && python3 -m venv env \
    && echo "source /work/env/bin/activate" >> ~/.bashrc
COPY requirements.txt /tmp/
RUN . /work/env/bin/activate \
    && pip install --upgrade pip \
    && pip install -r /tmp/requirements.txt
COPY . /tmp/

# # OpenImageIO
RUN apt-get update && apt-get install libjpeg-turbo8-dev
RUN mkdir -p /root/local/src \
    && cd /root/local/src \
    && git clone https://github.com/OpenImageIO/oiio.git -b v2.4.6.0\
    && cd oiio \
    && mkdir build \
    && cd build \
    && cmake -DCMAKE_INSTALL_PREFIX=/usr/local -DPYTHON_VERSION=3.10 -DUSE_PYTHON=1 -DVERBOSE=1 -DSTOP_ON_WARNING=0 .. \
    && make install -j4 \
    && make clean
ENV PYTHONPATH="/usr/local/lib/python3.8/site-packages"

# Install OpenColorIO
RUN apt-get update && apt-get install freeglut3-dev libglew-dev -y
RUN mkdir -p /root/local/src \
    && . /work/env/bin/activate \
    && cd /root/local/src \
    && git clone https://github.com/imageworks/OpenColorIO.git -b v2.2.0 \
    && mkdir -p /tmp/ociobuild \
    && cd /tmp/ociobuild \
    && cmake -DCMAKE_INSTALL_PREFIX=/usr/local /root/local/src/OpenColorIO \
    && make -j8 \
    && make install

# Install CTL
RUN cd /root/local/src \
    && git clone https://github.com/ampas/CTL.git \
    && cd CTL \
    && mkdir build && cd build && cmake .. && make && make install

# Install SampleICC
RUN cd /root/local/src \
    && wget https://sourceforge.net/projects/sampleicc/files/sampleicc%20tar/SampleIcc-1.6.8/SampleICC-1.6.8.tar.gz \
    && tar xvzf SampleICC-1.6.8.tar.gz \
    && cd SampleICC-1.6.8 \
    && ./configure \
    && make -j8 \
    && make install

# Install IccXML
RUN cd /root/local/src \
    && wget https://sourceforge.net/projects/iccxml/files/IccXML-Src/IccXML-0.9.8/IccXML-0.9.8.tar.gz \
    && tar -xzf IccXML-0.9.8.tar.gz \
    && cd IccXML-0.9.8 \
    && ./configure \
    && make -j8 \
    && make install

# Added /etc/ld.so.conf
RUN echo "/usr/local/lib" >> /etc/ld.so.conf \
    && ldconfig

RUN mkdir -p /root/local/src \
    && cd /root/local/src \
    && git clone https://github.com/AOMediaCodec/libavif.git -b v0.11.1 libavif_aom \
    && cd /root/local/src/libavif_aom/ext \
    && $SHELL ./libyuv.cmd \
    && $SHELL ./libjpeg.cmd \
    && $SHELL ./aom.cmd \
    && cd /root/local/src/libavif_aom/ \
    && mkdir build && cd build \
    && cmake .. -G Ninja -DCMAKE_BUILD_TYPE=Release -DBUILD_SHARED_LIBS=OFF -DAVIF_CODEC_AOM=ON -DAVIF_LOCAL_AOM=ON -DAVIF_LOCAL_JPEG=ON -DAVIF_LOCAL_LIBYUV=ON -DAVIF_BUILD_TESTS=1 -DAVIF_BUILD_APPS=1 \
    && ninja \
    && ninja install

# Install Noto Fonts
RUN mkdir font_install \
    && cd font_install \
    && curl -OL https://noto-website-2.storage.googleapis.com/pkgs/NotoSansCJKjp-hinted.zip \
    && unzip NotoSansCJKjp-hinted.zip \
    && mkdir -p /usr/share/fonts/opentype/noto \
    && cp *otf /usr/share/fonts/opentype/noto \
    && fc-cache -f -v \
    && cd .. \
    && rm -rf font_install

# Install BUZ Fonts
RUN mkdir /home/font_install \
    && cd /home/font_install \
    && git clone https://github.com/googlefonts/morisawa-biz-ud-gothic.git \
    && cd morisawa-biz-ud-gothic/fonts/ttf/ \
    && mkdir -p /usr/share/fonts/opentype/bizudp \
    && cp *.ttf /usr/share/fonts/opentype/bizudp \
    && fc-cache -f -v \
    && rm -rf /home/font_install/morisawa-biz-ud-gothic

# Git init settings
RUN git config --global user.name toru.yoshihara \
    && git config --global user.email toru.ver.11@gmail.com \
    && git config --global core.autocrlf true

# Clean
RUN apt-get clean \
    && rm -rf /var/lib/apt/lists/* \
    && rm -rf /roor/local/src
