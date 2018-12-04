FROM ubuntu:18.04
MAINTAINER Jamiel Sharief

ENV DATE_TIMEZONE UTC
ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update
RUN apt-get -y upgrade

RUN apt-get install -y mysql-server
RUN mkdir /var/run/mysqld
RUN chown -R mysql:mysql /var/run/mysqld

VOLUME /var/lib/mysql
VOLUME /etc/mysql

WORKDIR /data

EXPOSE 3306

CMD ["mysqld_safe"]
