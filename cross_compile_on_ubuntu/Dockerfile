FROM ubuntu:18.04

# Install OpenImageIO
RUN apt-get update && apt-get -y install \
    git \
    build-essential \
    mingw-w64

# Git init settings
RUN git config --global user.name toru.yoshihara \
    && git config --global user.email toru.ver.11@gmail.com

# Clean
RUN apt-get clean \
    && rm -rf /var/lib/apt/lists/*

CMD ["g++", "--version"]
