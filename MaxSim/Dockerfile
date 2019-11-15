FROM ubuntu:14.04
MAINTAINER Dongjoo Seo <djseo3@uci.edu> 

ENV SRC_PATH=/usr/local/src
ENV BIN_PATH=/usr/local/bin
ENV ARCH=amd64
ENV WORKDIR=$SRC_PATH/workdir
ENV JAVA=openjdk-7

RUN apt-get update && apt-get install -y wget sudo build-essential gcc g++ gdb git && rm -rf /var/lib/apt/lists/*

RUN apt-get update && apt-get install -y software-properties-common debconf-utils && rm -rf /var/lib/apt/lists/*

RUN echo "\ndeb http://old-releases.ubuntu.com/ubuntu/ saucy main" >> /etc/apt/sources.list

RUN apt-get update && apt-get install -y openjdk-7-jre-lib=7u25-2.3.12-4ubuntu3 openjdk-7-jre-headless=7u25-2.3.12-4ubuntu3 openjdk-7-jre=7u25-2.3.12-4ubuntu3 openjdk-7-jdk=7u25-2.3.12-4ubuntu3 && rm -rf /var/lib/apt/lists/*

ENV JAVA_HOME=/usr/lib/jvm/java-7-openjdk-amd64/
RUN java -version

WORKDIR $BIN_PATH
COPY protobuf-2.6.1.tar.gz $BIN_PATH/.
RUN tar xzf protobuf-2.6.1.tar.gz
RUN rm protobuf-2.6.1.tar.gz
ENV PROTOBUFPATH=$BIN_PATH/protobuf-2.6.1
WORKDIR $PROTOBUFPATH
RUN ./configure
RUN make && make check && make install
RUN ldconfig
ENV PROTOBUFPATH=/usr/local/
RUN rm -rf protobuf-2.6.1 && protoc --version

ENV MCPATPATH=$BIN_PATH/mcpat
COPY McPAT_v1.0.tar.gz $BIN_PATH/McPAT_v1.0.tar.gz
WORKDIR $BIN_PATH
RUN tar -xvzf McPAT_v1.0.tar.gz
RUN rm McPAT_v1.0.tar.gz
WORKDIR $MCPATPATH
RUN apt-get update && apt-get install -y gcc-multilib g++-multilib && rm -rf /var/lib/apt/lists/*
RUN make

RUN apt-get update && apt-get install -y mercurial zsh python2.7 && rm -rf /var/lib/apt/lists/*

ENV MAXSIM_SRC=$SRC_PATH/MaxSim
ENV MAXINE_HOME=$MAXSIM_SRC/maxine
ENV GRAAL_HOME=$MAXINE_SRC/graal

ENV PATH=$PATH:$GRAAL_HOME/mxtool/:$MAXINE_HOME/com.oracle.max.vm.native/generated/linux/

RUN git clone https://github.com/Sebastian-G/MaxSim $MAXSIM_SRC
WORKDIR $MAXSIM_SRC

RUN apt-get update && apt-get install -y scons libelf-dev libconfig++-dev libconfig-dev libconfig-dbg libconfig++-dbg libhdf5-dev && rm -rf /var/lib/apt/lists/*

COPY pin-2.14-71313-gcc.4.4.7-linux.tar.gz $BIN_PATH/pin-2.14-71313-gcc.4.4.7-linux.tar.gz
WORKDIR $BIN_PATH
RUN chmod ugo+x pin-2.14-71313-gcc.4.4.7-linux.tar.gz
RUN tar -xvzf pin-2.14-71313-gcc.4.4.7-linux.tar.gz
RUN rm $BIN_PATH/pin-2.14-71313-gcc.4.4.7-linux.tar.gz
RUN chmod 777 ./pin-2.14-71313-gcc.4.4.7-linux -R

ENV PINPATH=$BIN_PATH/pin-2.14-71313-gcc.4.4.7-linux
ENV LIBCONFIGPATH=/usr/local/lib
WORKDIR $MAXSIM_SRC

RUN ./scripts/buildMaxSimProduct.sh



