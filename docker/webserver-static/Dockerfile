# base container image
FROM ubuntu:18.04

# install packages
RUN export DEBIAN_FRONTEND=noninteractive && \
    apt update --fix-missing && apt upgrade -y && \
    apt install -y sudo locales nginx

# generate locale
RUN locale-gen en_US.UTF-8 && locale-gen --no-purge --lang en_US.UTF-8

# create a nginx user
RUN useradd -M --home /nonexistent --shell /usr/sbin/nologin nginx

# set default configuration
COPY nginx.conf /etc/nginx/nginx.conf

# default command at startup is nginx daemon
ENTRYPOINT [ "nginx" ]
