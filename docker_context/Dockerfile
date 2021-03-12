# https://hub.docker.com/_/ubuntu/
FROM ubuntu:20.10

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
######ADD openssl-1.1.1g.tar.gz /
######WORKDIR /openssl-1.1.1g
######RUN ./config --prefix=/usr && make -j && make -j install \
###### && rm -rf /openssl-1.1.1g
### STOP Install openssl 1.1.1g


### START Install Go 1.16.2
# https://golang.org/dl/go1.16.2.linux-amd64.tar.gz
ADD go1.16.2.linux-amd64.tar.gz /usr/local/
ENV PATH=$PATH:/usr/local/go/bin
### STOP Install go 1.16.2

RUN go version
RUN make --version
RUN python3 --version
