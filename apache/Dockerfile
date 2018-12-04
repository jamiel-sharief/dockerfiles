FROM ubuntu:18.04
MAINTAINER Jamiel Sharief

ENV DATE_TIMEZONE UTC
ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update
RUN apt-get -y upgrade

RUN apt-get -y install git zip unzip curl wget
RUN apt-get -y install apache2

# Enable apache mods.
RUN a2enmod rewrite
RUN a2enmod ssl

# Install PHP and Extensions
RUN apt-get install -y php php-cli
RUN apt-get install -y php-mysql libapache2-mod-php php-common php-curl php-pear php-mbstring php-json php-dom php-imap php-soap php-xml php-zip php-intl php-opcache php-apcu

# Install composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# Install PHP Unit
RUN wget https://phar.phpunit.de/phpunit-7.phar
RUN chmod +x phpunit-7.phar
RUN mv phpunit-7.phar /usr/local/bin/phpunit

ENV APACHE_RUN_USER www-data
ENV APACHE_RUN_GROUP www-data
ENV APACHE_LOG_DIR /var/log/apache2
ENV APACHE_LOCK_DIR /var/lock/apache2
ENV APACHE_PID_FILE /var/run/apache2.pid

VOLUME /var/www/html
VOLUME /var/log/apache2

EXPOSE 80 443

# Copy config and sample index file
ADD apache-config.conf /etc/apache2/sites-enabled/000-default.conf
ADD index.html /var/www/index.php

# Start Apache
CMD /usr/sbin/apache2ctl -D FOREGROUND
