FROM ubuntu:16.04

ENV APACHE_LOG_DIR="/var/log/apache2"
ENV LANG C.UTF-8

RUN apt-get update && apt-get install -y software-properties-common

RUN add-apt-repository -y -u ppa:ondrej/php

RUN apt-get update && apt-get install -y \
					curl \
					cron \
					unzip \
					git \
					apache2 \
					openssl \
					php7.1 \
					php7.1-cli \
					php7.1-fpm \
					php7.1-common \
					php7.1-curl \
					php7.1-gd \
					php7.1-mysql \
					php7.1-soap \
					php7.1-xml \
					php7.1-zip \
					php7.1-mbstring \
					php7.1-mcrypt \
					php7.1-intl \
					libapache2-mod-php7.1

#create ssl Cert
#ref : https://github.com/MarvAmBass/docker-apache2-ssl-secure
RUN mkdir -p /etc/apache2/external

RUN openssl req -x509 -newkey rsa:4086 \
  -subj "/C=XX/ST=XXXX/L=XXXX/O=XXXX/CN=localhost" \
  -keyout "/etc/apache2/external/key.pem" \
  -out "/etc/apache2/external/cert.pem" \
  -days 3650 -nodes -sha256

#install composer
RUN curl -sS https://getcomposer.org/installer -o composer-setup.php
RUN php composer-setup.php --install-dir=/bin --filename=composer

#enable apache mod
RUN a2enmod rewrite; \
    a2enmod ssl; \
    a2enmod headers;

#copy apache config
COPY ./000-default.conf /etc/apache2/sites-enabled/000-default.conf
COPY ./001-default-ssl.conf /etc/apache2/sites-enabled/001-default-ssl.conf

#copy apache run script
COPY ./run_script /usr/local/bin/run

RUN chmod +x /usr/local/bin/run

EXPOSE 80
EXPOSE 443
CMD ["/usr/local/bin/run"]