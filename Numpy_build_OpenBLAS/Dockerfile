FROM ubuntu:20.04

RUN apt-get update && apt-get install -y openssh-server
RUN mkdir /var/run/sshd
RUN echo 'root:Xi.eVkRu|+~&' | chpasswd
RUN sed -i 's/#PermitRootLogin prohibit-password/PermitRootLogin yes/' /etc/ssh/sshd_config

# SSH login fix. Otherwise user is kicked off after login
RUN sed 's@session\s*required\s*pam_loginuid.so@session optional pam_loginuid.so@g' -i /etc/pam.d/sshd

ENV NOTVISIBLE "in users profile"
RUN echo "export VISIBLE=now" >> /etc/profile

# EXPOSE 22
# CMD ["/usr/sbin/sshd", "-D"]

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
    gpac \
    libyaml-cpp-dev \
    libilmbase-dev \
    libxcomposite-dev \
    libxkbcommon-x11-dev \
    mesa-common-dev \
    imagemagick \
    python3-pip \
    python3-pybind11 \
    libwebp-dev \
    qt5dxcb-plugin \
    libxcb-icccm4 \
    libxcb-image0-dev \
    libxcb-keysyms1-dev \
    libxcb-randr0-dev \
    libxcb-render-util0-dev \
    libxcb-xinerama0-dev

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
    && echo "source /work/env/bin/activate" >> ~/.bash_profile
RUN apt-get update && apt-get -y install gfortran
RUN . /work/env/bin/activate \
    && pip install cython

RUN mkdir -p /root/local/src
RUN cd /root/local/src \
    && git clone https://github.com/xianyi/OpenBLAS.git \
    && cd OpenBLAS \
    && make FC=gfortran \
    && make install

RUN cd /root/local/src \
    && git clone https://github.com/numpy/numpy.git -b v1.21.0
COPY site.cfg /root/local/src/numpy/
RUN . /work/env/bin/activate \
    && cd /root/local/src/numpy \
    && python setup.py build -j 28 \
    && python setup.py install

# COPY requirements.txt /tmp/
# RUN . /work/env/bin/activate \
#     && pip install --upgrade pip \
#     && pip install -r /tmp/requirements.txt
# COPY . /tmp/

# Install Noto Fonts
# RUN mkdir font_install \
#     && cd font_install \
#     && curl -OL https://noto-website-2.storage.googleapis.com/pkgs/NotoSansCJKjp-hinted.zip \
#     && unzip NotoSansCJKjp-hinted.zip \
#     && mkdir -p /usr/share/fonts/opentype/noto \
#     && cp *otf /usr/share/fonts/opentype/noto \
#     && fc-cache -f -v \
#     && cd .. \
#     && rm -rf font_install

# # Git init settings
RUN git config --global user.name toru.yoshihara \
    && git config --global user.email toru.ver.11@gmail.com \
    && git config --global core.autocrlf true

# # Clean
# RUN apt-get clean \
#     && rm -rf /var/lib/apt/lists/* \
#     && rm -rf /roor/local/src
