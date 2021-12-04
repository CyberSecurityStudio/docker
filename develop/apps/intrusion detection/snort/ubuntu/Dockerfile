FROM ubuntu:latest

RUN apt update -y && apt upgrade -y
ARG DEBIAN_FRONTEND=noninteractive
ENV TZ=Etc/UTC
RUN apt install -y tzdata

RUN apt-get install -y build-essential libpcap-dev libpcre3-dev libdumbnet-dev bison flex zlib1g-dev liblzma-dev openssl libssl-dev libnghttp2-dev libnetfilter-queue-dev wget
RUN cd && wget http://luajit.org/download/LuaJIT-2.0.5.tar.gz && tar -zxvf LuaJIT-2.0.5.tar.gz && cd LuaJIT-2.0.5 && make && make install
RUN cd && wget https://snort.org/downloads/snort/daq-2.0.7.tar.gz && tar -zxvf daq-2.0.7.tar.gz && cd daq-2.0.7 && ./configure && make && make install
RUN cd && wget https://snort.org/downloads/snort/snort-2.9.18.1.tar.gz && tar -zxvf snort-2.9.18.1.tar.gz && cd snort-2.9.18.1 && ./configure && make && make install
RUN cd && ldconfig && ln -s /usr/local/bin/snort /usr/sbin/snort

RUN cd && rm -rf daq-2.0.7 && rm -rf snort-2.9.18.1 && rm -rf LuaJIT-2.0.5
RUN cd && rm -f *.tar.gz
