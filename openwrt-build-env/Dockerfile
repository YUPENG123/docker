# https://github.com/P3TERX/openwrt-build-env
# OpenWrt build environment in docker
# MIT License
# Copyright (c) 2020 P3TERX <https://p3terx.com>
# https://github.com/P3TERX/openwrt-build-env

# ARG BASE_IMAGE_TAG=20.04
ARG BASE_IMAGE_TAG=latest
# FROM linuxplus/ubuntu:${BASE_IMAGE_TAG}
FROM yupeng123456/ubuntu-plus:${BASE_IMAGE_TAG}

USER root

ARG DEBIAN_FRONTEND=noninteractive
ARG DEPENDS_LIST=depends-ubuntu-2004

RUN apt-get update -qq && \
    apt-get upgrade -qqy && \
    apt-get install -qqy build-essential clang flex bison gawk gettext \
    git-core gperf libncurses-dev libssl-dev libxml-parser-perl \
    python3-setuptools rsync subversion swig time wget zlib1g-dev \
    unzip libelf-dev qemu-utils upx-ucl libc6-dev  && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*
    # apt-get install -qqy $(curl -fsSL git.io/${DEPENDS_LIST}) && \

USER ubuntu
WORKDIR /home/ubuntu
