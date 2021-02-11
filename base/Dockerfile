FROM ubuntu:18.04

MAINTAINER m4j0rt0m

# install prerequisite software
RUN apt-get update && \
    DEBIAN_FRONTEND=noninteractive apt-get install -y \
    git make autoconf g++ flex bison \
    gperf libreadline6-dev libncurses5-dev && \
    apt-get clean

ENV DOCK /opt/docker
RUN mkdir $DOCK
WORKDIR $DOCK

# install icarus verilog
RUN cd $DOCK && \
    git clone https://github.com/steveicarus/iverilog.git iverilog && \
    cd iverilog && \
    autoconf && \
    ./configure && \
    make && \
    make check && \
    make install

# remove downloaded stuff
RUN cd $DOCK && \
    rm -rf iverilog

# force the use of bash
RUN ln -sf /bin/bash /bin/sh

WORKDIR /root
