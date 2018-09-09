FROM centos:7.5.1804
RUN yum -y update && \
    yum reinstall -y glibc-common && \
    localedef -v -c -i ja_JP -f UTF-8 ja_JP.UTF-8; echo "";
ENV LANG=ja_JP.UTF-8
ENV HOME="/root"
ENV PYENV_ROOT="$HOME/.pyenv"
RUN yum -y install gcc zlib-devel bzip2 bzip2-devel readline readline-devel sqlite sqlite-devel openssl openssl-devel git tk-devel && \
    git clone https://github.com/pyenv/pyenv.git "$HOME/.pyenv" && \
    echo -e 'if command -v pyenv 1>/dev/null 2>&1; then\n  eval "$(pyenv init -)"\nfi' >> ~/.bash_profile
ENV PATH="$PYENV_ROOT/bin:$PATH"
ENV PYTHONPATH="/work/lib"
RUN eval "$(pyenv init -)" && \
    pyenv install 3.6.6 && \
    pyenv global 3.6.6
RUN yum -y install libSM libXrender libXext
RUN echo -e 'opencv-python\n cycler\n numpy\n matplotlib\n scipy\n colour-science\n pillow' > requirements.txt && \
    eval "$(pyenv init -)" && \
    pip install -r requirements.txt
# install OpenImageIO
RUN yum -y install boost LibRaw gcc-c++ libtool aclocal autoheader automake autoconf libpng-devel
RUN yum -y install centos-release-scl-rh && \
    yum -y install devtoolset-7
RUN mkdir -p /root/local/src && \
    cd /root/local/src && \
    git clone https://gitlab.kitware.com/cmake/cmake.git && \
    cd cmake && \
    ./bootstrap && make && make install && \
    cd .. && \
    git clone https://gitlab.com/libtiff/libtiff.git && \
    cd libtiff && \
    ./autogen.sh && ./configure && make && make install &&\
    cd .. && \
    git clone https://github.com/openexr/openexr.git && \
    cd openexr && \
    cd OpenEXR && \
    ./bootstrap && ./configure && make && make install && \
    cd IlmBase && \
    ./bootstrap && ./configure && make && make install && \
    cd ../OpenEXR && \
    ./bootstrap && ./configure && make && make install && \
    cd ../../ && \
    git clone https://github.com/OpenImageIO/oiio.git && \
    cd oiio && \
    mkdir build && cd build && cmake ..

CMD ["python", "--version"]
