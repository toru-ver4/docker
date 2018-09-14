FROM fedora:28
# RUN yum -y update && \
#     yum reinstall -y glibc-common && \
#     localedef -v -c -i ja_JP -f UTF-8 ja_JP.UTF-8; echo "";
# ENV LANG=ja_JP.UTF-8
ENV HOME="/root"
ENV PYENV_ROOT="$HOME/.pyenv"
RUN yum -y install gcc zlib-devel bzip2 bzip2-devel readline readline-devel sqlite sqlite-devel openssl openssl-devel git tk-devel && \
    yum -y groupinstall 'Development Tools' && \
    git clone https://github.com/pyenv/pyenv.git "$HOME/.pyenv" && \
    echo -e 'if command -v pyenv 1>/dev/null 2>&1; then\n  eval "$(pyenv init -)"\nfi' >> ~/.bashrc
ENV PATH="$PYENV_ROOT/bin:$PATH"
ENV PYTHONPATH="/work/lib"
RUN eval "$(pyenv init -)" && \
    pyenv install 3.6.6 && \
    pyenv global 3.6.6
RUN yum -y install libSM libXrender libXext
RUN echo -e 'opencv-python\n cycler\n numpy\n matplotlib\n scipy\n colour-science\n pillow\n pybind11' > requirements.txt && \
    eval "$(pyenv init -)" && \
    pip install --upgrade pip && \
    pip install -r requirements.txt
# RUN eval "$(pyenv init -)" && \
#     python -m pip install pip==9.0.3
#     pip install pybind
# install OpenImageIO
RUN yum -y install boost-devel LibRaw gcc-c++ libtool automake autoconf cmake libpng-devel libtiff OpenEXR-devel libtiff-devel libjpeg-turbo-devel
ENV PYTHON_EXECUTABLE="/root/.pyenv/versions/3.6.6/bin"
ENV PYTHON_INCLUDE_DIRS="/root/.pyenv/versions/3.6.6/include"
ENV PYTHON_LIBRARIES="/root/.pyenv/versions/3.6.6/lib"
RUN mkdir -p /root/local/src && \
    cd /root/local/src && \
    git clone https://github.com/OpenImageIO/oiio.git && \
    cd oiio && \
    mkdir build && cd build && \
    cmake \
    -DPYTHON_INCLUDE_DIRS="/root/.pyenv/versions/3.6.6/include" \
    -DPYTHON_LIBRARIES="/root/.pyenv/versions/3.6.6/lib" .. \


CMD ["python", "--version"]
