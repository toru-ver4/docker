FROM ubuntu:20.04

RUN apt-get update && apt-get install -y openssh-server
RUN mkdir /var/run/sshd
RUN echo 'root:Xi.eVkRu|+~&' | chpasswd
RUN sed -i 's/#PermitRootLogin prohibit-password/PermitRootLogin yes/' /etc/ssh/sshd_config

# SSH login fix. Otherwise user is kicked off after login
RUN sed 's@session\s*required\s*pam_loginuid.so@session optional pam_loginuid.so@g' -i /etc/pam.d/sshd

ENV NOTVISIBLE "in users profile"
RUN echo "export VISIBLE=now" >> /etc/profile

EXPOSE 22
CMD ["/usr/sbin/sshd", "-D"]

# Install OpenImageIO
RUN apt-get update && apt-get -y install \
    g++ \
    gdb \
    git \
    software-properties-common \
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
    cmake \
    python3-pybind11

RUN mkdir -p /root/local/src \
    && cd /root/local/src \
    && git clone https://github.com/OpenImageIO/oiio.git \
    && cd oiio \
    && mkdir build \
    && cd build \
    && cmake -DCMAKE_INSTALL_PREFIX=/usr/local -DPYTHON_VERSION=3.8 -DVERBOSE=1 -DSTOP_ON_WARNING=0 .. \
    && make install -j4 \
    && make clean
ENV PYTHONPATH="/usr/local/lib/python3.8/site-packages"

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
RUN mkdir /work && cd /work \
    && python3 -m venv env \
    && echo "source /work/env/bin/activate" >> ~/.bashrc
COPY requirements.txt /tmp/
RUN . /work/env/bin/activate \
    && pip install --upgrade pip \
    && pip install -r /tmp/requirements.txt
COPY . /tmp/

# Install OpenColorIO
RUN apt-get update && apt-get install freeglut3-dev libglew-dev -y
RUN mkdir -p /root/local/src \
    && . /work/env/bin/activate \
    && cd /root/local/src \
    && git clone https://github.com/imageworks/OpenColorIO.git \
    && mkdir -p /tmp/ociobuild \
    && cd /tmp/ociobuild \
    && cmake -DCMAKE_INSTALL_PREFIX=/usr/local /root/local/src/OpenColorIO \
    && make -j8 \
    && make install

# Install CTL
RUN cd /root/local/src \
    && git clone https://github.com/toru-ver4/CTL.git \
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

# Git init settings
RUN git config --global user.name toru.yoshihara \
    && git config --global user.email toru.ver.11@gmail.com \
    && git config --global core.autocrlf true

# Clean
RUN apt-get clean \
    && rm -rf /var/lib/apt/lists/* \
    && rm -rf /roor/local/src
