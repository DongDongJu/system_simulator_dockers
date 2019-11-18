FROM ubuntu:16.04
MAINTAINER Dongjoo Seo <dseo3@uci.edu>
RUN apt-get update && \
        apt-get install -y \
        build-essential \
        cmake \
        git \
        wget \
        unzip \
        yasm \
        pkg-config \
        libswscale-dev \
        libtbb2 \
        libtbb-dev \
        libjpeg-dev \
        libpng-dev \
        libtiff-dev \
        libjasper-dev \
        libavformat-dev \
        libpq-dev \
	python-pip \
        python2.7 \
        python2.7-dev

COPY requirements.txt ./
RUN pip install --no-cache-dir -r requirements.txt


RUN wget https://github.com/opencv/opencv/archive/2.4.13.3.zip \
&& unzip 2.4.13.3.zip \
&& mkdir /opencv-2.4.13.3/cmake_binary \
&& cd /opencv-2.4.13.3/cmake_binary \
&& cmake -DWITH_QT=OFF \
        -DWITH_OPENGL=ON \
        -DFORCE_VTK=OFF \
        -DWITH_TBB=ON \
        -DWITH_GDAL=ON \
        -DWITH_XINE=ON \
        -DBUILD_EXAMPLES=OFF \
        -DENABLE_PRECOMPILED_HEADERS=OFF .. \
&& make install \
&& rm /2.4.13.3.zip \
&& rm -r /opencv-2.4.13.3

RUN dpkg --add-architecture i386
RUN apt-get update && apt-get install -y python binutils build-essential curl git libboost-dev libncurses5:i386 libsqlite3-dev libstdc++6:i386 python wget zlib1g-dev libbz2-dev screen tmux binutils libc6:i386 libncurses5:i386 libstdc++6:i386 && rm -rf /var/lib/apt/lists/*

RUN apt-get update && apt-get install -y automake build-essential curl wget libboost-dev libsqlite3-dev zlib1g-dev libbz2-dev g++-4.8 g++-4.9 git && rm -rf /var/lib/apt/lists/*

ENV PIN_NAME pin-3.11-97998-g7ecce2dac-gcc-linux
WORKDIR /usr/local/bin
RUN wget https://software.intel.com/sites/landingpage/pintool/downloads/pin-3.11-97998-g7ecce2dac-gcc-linux.tar.gz
RUN chmod ugo+x $PIN_NAME.tar.gz
RUN tar -xvzf $PIN_NAME.tar.gz
RUN rm /usr/local/bin/$PIN_NAME.tar.gz
RUN chmod 777 ./$PIN_NAME -R
ENV PIN_HOME /usr/local/bin/$PIN_NAME

RUN mkdir /usr/local/src/sniper
WORKDIR /usr/local/src/sniper
COPY sniper-7.2.tgz ./
RUN tar xvf sniper-7.2.tgz
ENV SNIPER_PATH=/usr/local/src/sniper/sniper-7.2
WORKDIR $SNIPER_PATH
RUN make -j2

