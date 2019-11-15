FROM ubuntu:16.04

RUN dpkg --add-architecture i386
RUN apt-get update && apt-get install -y python screen tmux binutils libc6:i386 libncurses5:i386 libstdc++6:i386 && rm -rf /var/lib/apt/lists/*

RUN apt-get update && apt-get install -y automake build-essential curl wget libboost-dev libsqlite3-dev zlib1g-dev libbz2-dev g++-4.8 g++-4.9 git && rm -rf /var/lib/apt/lists/*

ENV PIN_NAME=pin-3.5-97503-gac534ca30-gcc-linux
COPY $PIN_NAME.tar.gz /usr/local/bin/$PIN_NAME.tar.gz
WORKDIR /usr/local/bin
RUN chmod ugo+x $PIN_NAME.tar.gz
RUN tar -xvzf $PIN_NAME.tar.gz
RUN rm /usr/local/bin/$PIN_NAME.tar.gz
RUN chmod 777 ./$PIN_NAME -R
ENV PIN_HOME /usr/local/bin/$PIN_NAME

WORKDIR /usr/local/src/
RUN git clone http://snipersim.org/download/217c2c1a0b688705/git/sniper.git
ENV SNIPER_PATH=/usr/local/src/sniper
WORKDIR /usr/local/src/sniper
RUN make

