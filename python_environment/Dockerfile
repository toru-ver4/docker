FROM fedora:28
RUN yum -y install libSM libXrender libXext libstdc++-devel python3-tkinter
RUN python3 -m venv /work && \
    echo -e "source /work/bin/activate" >> ~/.bashrc
ENV PYTHONPATH="/work/src/lib"
RUN source /work/bin/activate && \
    echo -e 'opencv-python\n cycler\n numpy\n matplotlib\n scipy\n colour-science\n pillow\n pybind11' > requirements.txt && \
    pip install --upgrade pip && \
    pip install -r requirements.txt

# install OpenImageIO
RUN yum -y install boost-python3-devel LibRaw gcc-c++ libtool automake autoconf make cmake libpng-devel libtiff OpenEXR-devel libtiff-devel libjpeg-turbo-devel git
RUN mkdir -p /root/local/src && \
    cd /root/local/src && \
    git clone https://github.com/OpenImageIO/oiio.git && \
    cd oiio && \
    mkdir build && cd build && \
    cmake -DPYTHON_VERSION=3.6 \
    -DPYTHON_INCLUDE_DIR=$(python -c "from distutils.sysconfig import get_python_inc; print(get_python_inc())") \
    -DPYTHON_LIBRARY=$(python -c "import distutils.sysconfig as sysconfig; print(sysconfig.get_config_var('LIBDIR'))") ..

CMD ["python", "--version"]

# FROM ubuntu:18.04
# RUN apt-get update && \
# ENV PATH="$PATH:/root/local/src/oiio/dist/linux64/bin"
# ENV LD_LIBRARY_PATH="$LD_LIBRARY_PATH:/root/local/src/oiio/dist/linux64/lib"
# ENV PYTHONPATH="/work/src/lib:/root/local/src/oiio/dist/linux64/lib/python3.6/site-packages"