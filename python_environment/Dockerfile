FROM ubuntu:18.04

# Install OpenImageIO
RUN apt-get update && apt-get -y install \
    cmake \
    g++ \
    gdb \
    git \
    software-properties-common \
    libtiff5-dev \
    libboost-all-dev \
    libpng-dev \
    libopenexr-dev \
    libraw-dev \
    ffmpeg \
    libopenjp2-7-dev \
    curl \
    unzip
RUN mkdir -p /root/local/src \
    && cd /root/local/src \
    && git clone https://github.com/OpenImageIO/oiio.git \
    && cd oiio \
    && mkdir build \
    && cd build \
    && cmake -DCMAKE_INSTALL_PREFIX=/usr/local -DPYTHON_VERSION=3.6 -DVERBOSE=1 -DSTOP_ON_WARNING=0 .. \
    && make install -j4 \
    && make clean
ENV PYTHONPATH="/usr/local/lib/python3.6/site-packages"

# Install Basic Python Libraries
ENV DEBIAN_FRONTEND=noninteractive
RUN apt-get update && apt-get -y install tzdata
ENV TZ Asia/Tokyo
RUN apt-get update \
    && apt-get upgrade -y \
    && apt-get install -y \
    tzdata
RUN apt-get update && apt-get -y install \
    python3-venv \
    libsm-dev \
    libxrender-dev \
    python3-tk
RUN python3 -m venv /work && \
    echo "source /work/bin/activate" >> ~/.bashrc
ENV PYTHONPATH="$PYTHONPATH:/work/src/lib"
COPY requirements.txt /tmp/
RUN . /work/bin/activate \
    && pip install --upgrade pip \
    && pip install -r /tmp/requirements.txt
COPY . /tmp/

# Install OpenColorIO
RUN apt-get install freeglut3-dev libglew-dev -y
RUN mkdir -p /root/local/src \
    && cd /root/local/src \
    && git clone https://github.com/imageworks/OpenColorIO.git \
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

# Install ImageMagick
RUN apt-get update \
    && apt-get install -y imagemagick

# Clean
RUN apt-get clean \
    && rm -rf /var/lib/apt/lists/*

CMD ["python", "--version"]
