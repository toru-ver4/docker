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
    && cmake -DCMAKE_INSTALL_PREFIX=/usr/local -DPYTHON_VERSION=3.6 -DVERBOSE=1 -DSTOP_ON_WARNING=0 .. \
    && make clean
    # && make PYTHON_VERSION=3.6 VERBOSE=1 STOP_ON_WARNING=0 \
    
# ENV PATH="$PATH:/root/local/src/oiio/dist/linux64/bin"
# ENV LD_LIBRARY_PATH="$LD_LIBRARY_PATH:/root/local/src/oiio/dist/linux64/lib"
# ENV PYTHONPATH="/root/local/src/oiio/dist/linux64/lib/python3.6/site-packages"
# ENV PYTHONPATH="/usr/local/lib/python3.6/site-packages"

# Install Basic Python Libraries
ENV DEBIAN_FRONTEND=noninteractive
RUN apt-get -y install tzdata
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

# export OIIO_LIBRARIES="/root/local/src/oiio"
ENV OIIO_INCLUDE_DIR="/root/local/src/oiio/dist/linux64/include"
# export OIIO_LIBRARY_DIR=""
RUN mkdir -p /root/local/src \
    && cd /root/local/src \
    && git clone https://github.com/imageworks/OpenColorIO.git \
    && mkdir -p /opt/ocio \
    && mkdir -p /tmp/ociobuild \
    && cd /tmp/ociobuild \
    && cmake -DCMAKE_INSTALL_PREFIX=/usr/local /root/local/src/OpenColorIO

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
