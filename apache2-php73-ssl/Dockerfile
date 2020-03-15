FROM ubuntu:19.10
ENV DEBIAN_FRONTEND="noninteractive"
ENV APACHE_LOG_DIR="/var/log/apache2"
ENV LANG C.UTF-8

RUN apt-get update && apt-get install -y software-properties-common

RUN add-apt-repository -y -u ppa:ondrej/php

RUN apt-get update && apt-get install -y \
					curl \
					cron \
					unzip \
					git \
					npm \
					nodejs \
					apache2 \
					openssl \
					php7.3 \
					php7.3-cli \
					php7.3-fpm \
					php7.3-common \
					php7.3-curl \
					php7.3-gd \
					php7.3-mysql \
					php7.3-soap \
					php7.3-xml \
					php7.3-zip \
					php7.3-mbstring \
					php7.3-intl \
					php7.3-json \
					libapache2-mod-php7.3
					
					

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