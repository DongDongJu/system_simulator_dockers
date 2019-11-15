FROM ubuntu:14.04
MAINTAINER Dongjoo Seo <djseo3@uci.edu> 

RUN apt-get update
RUN apt-get install -y build-essential git-core automake autoconf libtool zlib1g-dev lib32gcc1 gcc-multilib libgtk-3-dev
RUN apt-get clean

WORKDIR /usr/local/src
RUN git clone https://github.com/Multi2Sim/multi2sim.git
WORKDIR /usr/local/src/multi2sim

RUN libtoolize
RUN aclocal
RUN autoconf
RUN automake --add-missing
RUN ./configure
RUN make
RUN make install

WORKDIR /usr/local/src/multi2sim/samples/x86/example-1
RUN m2s test-args how are you
ENTRYPOINT bash

