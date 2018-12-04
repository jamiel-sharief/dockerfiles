FROM ubuntu:latest
MAINTAINER Jamiel Sharief

ENV DATE_TIMEZONE UTC
ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update
RUN apt-get  -y upgrade

RUN apt-get install -y openssh-server
RUN mkdir /var/run/sshd

RUN apt-get install -y sudo
RUN useradd -d /home/developer -ms /bin/bash developer
RUN echo 'developer:password' | chpasswd
RUN usermod -aG sudo developer

EXPOSE 22

CMD /usr/sbin/sshd -D
