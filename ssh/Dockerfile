FROM ubuntu:18.04
MAINTAINER Jamiel Sharief

ENV DATE_TIMEZONE UTC
ENV DEBIAN_FRONTEND=noninteractive

# Best Practice : Cache Busting - Prevent cache issues run as one command
# @link https://docs.docker.com/develop/develop-images/dockerfile_best-practices/

RUN apt-get update && apt-get install -y \
    openssh-server \
    sudo \
 && rm -rf /var/lib/apt/lists/*

RUN mkdir /var/run/sshd

RUN useradd -d /home/developer -ms /bin/bash developer
RUN echo 'developer:password' | chpasswd
RUN usermod -aG sudo developer

EXPOSE 22

CMD /usr/sbin/sshd -D
