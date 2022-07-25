# Build and run:
#   docker build -t clion/ubuntu/cpp-env:1.0 -f Dockerfile.cpp-env-ubuntu 

FROM ubuntu:latest

RUN DEBIAN_FRONTEND="noninteractive" apt-get update && apt-get -y install tzdata

RUN apt-get update \
  && apt-get install -y build-essential \
      gcc \
      g++ \
      gdb \
      clang \
      make \
      ninja-build \
      cmake \
      autoconf \
      automake \
      locales-all \
      dos2unix \
      rsync \
      tar \
  && apt-get clean

RUN apt-get install -y pkg-config
RUN apt-get install -y zlib1g zlib1g-dev

COPY . /tmp/
WORKDIR /tmp/
RUN ./configure
RUN make -j8
RUN make install

ENTRYPOINT ["/usr/local/bin/vcftools"]
