ARG base_image_version=0.10.0
FROM phusion/baseimage:$base_image_version

ENV TERM=xterm

RUN apt-get update

RUN apt-get install -y \
    apt-utils \
    git \
    vim \
    zsh \
    iputils-ping \
    net-tools \
    netcat

ARG LOCALE_LANG_COUNTRY="en_US"
ARG LOCALE_CODIFICATION="UTF-8"
ARG LOCALE_CODIFICATION_ENV="utf8"

RUN git clone git://github.com/robbyrussell/oh-my-zsh.git ~/.oh-my-zsh --depth 1 \
    && cp ~/.oh-my-zsh/templates/zshrc.zsh-template ~/.zshrc

ADD https://github.com/just-containers/s6-overlay/releases/download/v1.21.2.2/s6-overlay-amd64.tar.gz /tmp/
RUN tar xzf /tmp/s6-overlay-amd64.tar.gz -C /

ADD https://github.com/just-containers/socklog-overlay/releases/download/v2.1.0-0/socklog-overlay-amd64.tar.gz /tmp/
RUN tar xzf /tmp/socklog-overlay-amd64.tar.gz -C /



RUN apt-get install -y \
    build-essential \
    python-dev \
    gcc-4.9 \
    g++-4.9 \
    git cmake \
    libboost1.58-all-dev \
    librocksdb-dev

RUN apt-get install -y  \
    libboost-system1.58.0 \
    libboost-filesystem1.58.0 \
    libboost-thread1.58.0 \
    libboost-date-time1.58.0 \
    libboost-chrono1.58.0 \
    libboost-regex1.58.0 \
    libboost-serialization1.58.0 \
    libboost-program-options1.58.0 \
    libicu55

WORKDIR /node

COPY bin/catalystd .
