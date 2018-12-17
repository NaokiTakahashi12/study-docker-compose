FROM javierprovecho/docker-codebox

RUN apt update && \
    apt upgrade -y && \
    apt install -y \
    wget \
	vim \
	git \
	make \
	automake \
	build-essential \
	python-dev \
	python-pip \
	software-properties-common && \
    rm -rf /var/lib/apt/lists/*

RUN add-apt-repository ppa:ubuntu-toolchain-r/test && apt update && apt install -y g++-7 gcc-7

RUN mkdir build_space && cd build_space && \
    wget -O cmake.tar.gz https://github.com/Kitware/CMake/releases/download/v3.13.2/cmake-3.13.2.tar.gz && \
    wget -O boost.tar.bz2 https://dl.bintray.com/boostorg/release/1.69.0/source/boost_1_69_0.tar.bz2 && \
    wget -O eigen3.tar.bz2 http://bitbucket.org/eigen/eigen/get/3.3.7.tar.bz2 && \
    wget -O opencv.tar.gz https://github.com/opencv/opencv/archive/3.4.4.tar.gz && \
    tar xf boost.tar.bz2 && \
    tar xf cmake.tar.gz && \ 
    tar xf eigen3.tar.bz2 && \
    tar xf opencv.tar.gz

RUN cd build_space && \
    cd cmake-3.13.2 && ./bootstrap && make -j8 && make install
RUN cd build_space && \
    cd boost_1_69_0 && ./bootstrap.sh && ./b2 toolset=gcc-7 install -j6
RUN cd build_space && \
    cd eigen-eigen-323c052e1731 && mkdir build && cd build && cmake .. && make install
RUN cd build_space && \
    cd opencv-3.4.4 && mkdir build && cd build && cmake .. && make -j6 && make install

