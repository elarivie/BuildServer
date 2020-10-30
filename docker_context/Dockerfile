FROM ubuntu:20.04

ARG DEBIAN_FRONTEND=noninteractive

### START Install Ubuntu packages
RUN apt-get update && apt-get install -y \
  build-essential \
  curl \
  tzdata \
  zlib1g-dev \
  texlive-full \
 && rm -rf /var/lib/apt/lists/*
### STOP Install Ubuntu packages

### START Install make 4.3
# ftp://ftp.gnu.org/gnu/make/make-4.3.tar.gz
ADD make-4.3.tar.gz /
WORKDIR /make-4.3
RUN ./configure --prefix=/usr && make -j && make -j install \
 && rm -rf /make-4.3
### STOP Install make 4.3

### START Install openssl 1.1.1g
# https://www.openssl.org/source/openssl-1.1.1g.tar.gz
ADD openssl-1.1.1g.tar.gz /
WORKDIR /openssl-1.1.1g
RUN ./config --prefix=/usr && make -j && make -j install \
 && rm -rf /openssl-1.1.1g
### STOP Install openssl 1.1.1g

### START Install python 3.8
# https://www.python.org/ftp/python/3.8.3/Python-3.8.3rc1.tgz
ADD Python-3.8.3rc1.tgz /
WORKDIR /Python-3.8.3rc1
RUN ./configure --prefix=/usr --enable-optimizations --with-ensurepip=install && make -j && make -j install
WORKDIR /
RUN rm -rf /Python-3.8.3rc1 && python3 -m ensurepip --upgrade
RUN apt-get update && apt-get install -y python3-pip
### STOP Install python 3.8

