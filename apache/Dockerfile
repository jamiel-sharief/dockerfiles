FROM ubuntu:18.04
MAINTAINER Jamiel Sharief

ENV DATE_TIMEZONE UTC
ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update

RUN apt-get -y install curl git mysql-client nano unzip wget zip
RUN apt-get -y install apache2 libapache2-mod-php

RUN a2enmod rewrite
RUN a2enmod ssl

RUN apt-get install -y php php-cli
RUN apt-get install -y php-apcu php-cli php-common php-curl php-imap php-intl php-json php-mbstring php-mysql php-opcache php-pear php-readline php-soap php-xml php-zip

RUN rm -r /var/lib/apt/lists/*

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

RUN wget https://phar.phpunit.de/phpunit-7.phar
RUN chmod +x phpunit-7.phar
RUN mv phpunit-7.phar /usr/local/bin/phpunit

VOLUME /var/www/html
VOLUME /var/log/apache2

EXPOSE 80 443

ADD apache-config.conf /etc/apache2/sites-enabled/000-default.conf
ADD index.html /var/www/index.php

CMD /usr/sbin/apache2ctl -D FOREGROUND
