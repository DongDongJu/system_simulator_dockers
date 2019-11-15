FROM ubuntu:14.04
MAINTAINER Dongjoo Seo <djseo3@uci.edu>

RUN apt-get update
RUN apt-get install -y build-essential git-core scons gcc libelf-dev libconfig++-dev libconfig-dev libconfig-dbg libconfig++-dbg libhdf5-dev
RUN apt-get clean

RUN ln -s /usr/include/asm-generic /usr/include/asm

RUN apt-get install -y software-properties-common debconf-utils
RUN add-apt-repository -y ppa:webupd8team/java
RUN apt-get update
RUN apt-get install -y openjdk-7-jre

COPY pin-2.14-71313-gcc.4.4.7-linux.tar.gz /usr/local/bin/pin-2.14-71313-gcc.4.4.7-linux.tar.gz
WORKDIR /usr/local/bin
RUN chmod ugo+x pin-2.14-71313-gcc.4.4.7-linux.tar.gz
RUN tar -xvzf pin-2.14-71313-gcc.4.4.7-linux.tar.gz
RUN rm /usr/local/bin/pin-2.14-71313-gcc.4.4.7-linux.tar.gz
RUN chmod 777 ./pin-2.14-71313-gcc.4.4.7-linux -R

ENV PINPATH /usr/local/bin/pin-2.14-71313-gcc.4.4.7-linux

WORKDIR /usr/local/src
RUN git clone https://github.com/Sebastian-G/zsim.git
WORKDIR /usr/local/src/zsim
RUN git checkout linux-4.9

RUN scons -j16
WORKDIR /usr/local/src/zsim
ENTRYPOINT bash

