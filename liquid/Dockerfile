# Download base image ubuntu 16.04
FROM ubuntu:16.04

# Update Ubuntu Software repository
RUN apt-get update && apt-get install -y python-software-properties && apt-get install -y software-properties-common 

# Bitcoin PPA 
RUN apt-add-repository ppa:bitcoin/bitcoin
# Update Ubuntu Software repository
RUN apt-get update

# Bitcoin
RUN apt-get install -y bitcoind
RUN apt-get install -y git && apt-get install -y wget

# Liquid
RUN wget https://github.com/Blockstream/liquid/releases/download/liquid.3.14.1.21/liquid-3.14.1.21-x86_64-linux-gnu.tar.gz
RUN tar xvzf liquid-3.14.1.21-x86_64-linux-gnu.tar.gz
RUN mv liquid-3.14.1.21 /home/liquid

WORKDIR /home/liquid

ENTRYPOINT [ "./bin/liquidd" ]