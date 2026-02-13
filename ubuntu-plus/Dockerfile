#===================================================
# https://github.com/P3TERX/ubuntu-plus
# Description: Ubuntu image with some extra packages
# Lisence: MIT
# Author: P3TERX
# Blog: https://p3terx.com
#===================================================
ARG IMAGE_TAG=latest
FROM ubuntu:$IMAGE_TAG

LABEL maintainer=YUPENG

ARG DEBIAN_FRONTEND=noninteractive

RUN apt-get update -qq && apt-get upgrade -qqy && \
    apt-get install -qqy git wget htop tmux tree curl vim nano sudo ca-certificates zsh uuid-runtime tzdata  lrzsz xz-utils openssh-server && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* && \
    mkdir /var/run/sshd && \
    usermod  -aG sudo -s /usr/bin/zsh ubuntu && \
    echo 'ubuntu:ubuntu' | chpasswd && \
    echo 'ubuntu ALL=(ALL) NOPASSWD: ALL' > /etc/sudoers.d/ubuntu && \
    chmod 440 /etc/sudoers.d/ubuntu && \
    usermod -s /usr/bin/zsh root && \
    curl -fsSL git.io/tmate.sh | bash
    # curl -fsSL git.io/gotop.sh | bash -s install && \
    # curl -fsSL git.io/bashtop.sh | bash -s install
    # RUN apt-get install -qqy htop tmux tree curl vim nano
    # RUN apt-get install -qqy sudo ca-certificates zsh uuid-runtime tzdata  lrzsz xz-utils
    # RUN apt-get install -qqy openssh-server  && \

USER ubuntu
WORKDIR /home/ubuntu

RUN mkdir -p ~/.ssh && \
    chmod 700 ~/.ssh
    # curl -fsSL git.io/oh-my-zsh.sh | bash && \
    # curl -fsSL git.io/oh-my-tmux.sh | bash

ENV TZ=Asia/Shanghai \
    LANG=C.UTF-8

EXPOSE 22

CMD [ "sudo", "/usr/sbin/sshd", "-D" ]
