FROM ubuntu:latest
LABEL Name=bitcoin-docker Version=0.17
RUN apt-get -y update && apt-get install 
CMD /usr/games/fortune -a | cowsay

RUN apt-get update;\
	apt-get install -y \
		build-essential \
		libtool \
		autotools-dev \
		autoconf \
		ccache \
		pkg-config \
		libssl-dev \
		libboost-all-dev \
		wget \
		bsdmainutils \
		libqrencode-dev \
		libqt4-dev \
		libprotobuf-dev \
		protobuf-compiler \
		git \
		gdb \
		libevent-dev;

RUN apt-get install -y \
    gdbserver; \ 
  apt-get clean; \
	rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*
RUN git clone https://github.com/bitcoin/bitcoin.git /home/ubuntu/bitcoin
WORKDIR /home/ubuntu/bitcoin

RUN git checkout origin/0.17
ADD install_bdb.sh .
RUN ./install_bdb.sh
RUN ./autogen.sh && ./configure LDFLAGS="-L/home/ubuntu/bitcoin/db4/lib/" CPPFLAGS="-I/home/ubuntu/bitcoin/db4/include/" --enable-debug --with-gui=no && make -j6

ENTRYPOINT [ "bitcoind" ]