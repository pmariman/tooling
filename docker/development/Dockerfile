# base container image
FROM debian:buster

# install packages for development
RUN export DEBIAN_FRONTEND=noninteractive && \
    apt update && apt upgrade -y && \
    apt install -y sudo build-essential file git rsync unzip \
    wget curl vim procps silversearcher-ag man tmux locales \
    gawk tree cmake python3

# create a dev user and group
ARG USER_UID=1000
ARG USER_GID=1000
RUN groupadd --gid ${USER_GID} dev && \
    useradd -l -m dev --uid ${USER_UID} --gid ${USER_GID} && \
    adduser dev sudo && \
    (echo 'dev:dev' | chpasswd)

# generate locale
RUN locale-gen en_US.UTF-8 && locale-gen --no-purge --lang en_US.UTF-8

# set TERM variable to fix ncurses flickering
ENV TERM=xterm-color

# set start user and workdir
USER dev
WORKDIR /home/dev

# default command at startup is bash shell
CMD /bin/bash
