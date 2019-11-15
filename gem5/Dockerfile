FROM ubuntu:16.04
MAINTAINER Dongjoo Seo <djseo3@uci.edu>

RUN apt-get update
RUN apt-get install -y build-essential git-core m4 scons zlib1g zlib1g-dev libprotobuf-dev protobuf-compiler libprotoc-dev libgoogle-perftools-dev swig python-dev python python-six && rm -rf /var/lib/apt/lists/* 

RUN apt-get clean

WORKDIR /usr/local/src
RUN git clone https://github.com/gem5/gem5.git

WORKDIR /usr/local/src/gem5
ADD build.bash /usr/local/src/gem5/build.bash
RUN chmod ugo+x build.bash
RUN ./build.bash

ENV gem5 /usr/local/bin/gem5.opt
ENTRYPOINT bash
 
