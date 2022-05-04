# https://hub.docker.com/_/ubuntu/
FROM ubuntu:22.04

ARG DEBIAN_FRONTEND=noninteractive

### START Install Ubuntu packages
RUN apt-get update && apt-get install -y \
  build-essential \
  g++-mingw-w64-x86-64 \
  curl \
  git \
  inkscape \
  make \
  tzdata \
  zlib1g-dev \
  texlive-full \
 && rm -rf /var/lib/apt/lists/*
### STOP Install Ubuntu packages

### START Install Go 1.18.1
# https://golang.org/dl/go1.18.1.linux-amd64.tar.gz
ADD go1.18.1.linux-amd64.tar.gz /usr/local/
ENV PATH=$PATH:/usr/local/go/bin
### STOP Install go 1.18.1

RUN make --version
RUN python3 --version
RUN go version
