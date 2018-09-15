FROM ubuntu:18.04

# Install OpenImageIO
RUN apt-get update && \
    apt-get -y install cmake g++ gdb git software-properties-common \
    libtiff5-dev libboost-all-dev libpng-dev libopenexr-dev wget unzip
RUN mkdir -p /root/local/src && \
    cd /root/local/src && \
    git clone https://github.com/OpenImageIO/oiio.git && \
    cd oiio && \
    make PYTHON_VERSION=3.6 VERBOSE=1 STOP_ON_WARNING=0 && \
    make clean
ENV PATH="$PATH:/root/local/src/oiio/dist/linux64/bin"
ENV LD_LIBRARY_PATH="$LD_LIBRARY_PATH:/root/local/src/oiio/dist/linux64/lib"
ENV PYTHONPATH="/root/local/src/oiio/dist/linux64/lib/python3.6/site-packages"

# Install Basic Python Libraries
ENV DEBIAN_FRONTEND=noninteractive
RUN apt-get -y install tzdata
ENV TZ Asia/Tokyo
RUN apt-get update && \
    apt-get upgrade -y && \
    apt-get install -y \
    tzdata
RUN apt-get -y install python3-venv libsm-dev libxrender-dev python3-tk
RUN python3 -m venv /work && \
    echo "source /work/bin/activate" >> ~/.bashrc
ENV PYTHONPATH="$PYTHONPATH:/work/src/lib"
RUN . /work/bin/activate && \
    echo "opencv-python\n cycler\n numpy\n matplotlib\n scipy\n colour-science\n pillow\n sphinx_rtd_theme\n sympy" > requirements.txt && \
    pip install --upgrade pip && \
    pip install -r requirements.txt

CMD ["python", "--version"]
