FROM ubuntu:16.04

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

