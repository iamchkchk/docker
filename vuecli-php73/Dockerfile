FROM ubuntu:19.04
ENV DEBIAN_FRONTEND="noninteractive"
ENV LANG C.UTF-8

RUN apt-get update && apt-get install -y software-properties-common

RUN add-apt-repository -y -u ppa:ondrej/php

RUN apt-get update && apt-get install -y \
					curl \
					cron \
					unzip \
					npm \
					nodejs \
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
					php7.3-json 
					
#install composer
RUN curl -sS https://getcomposer.org/installer -o composer-setup.php
RUN php composer-setup.php --install-dir=/bin --filename=composer

#install laravel
RUN composer global require laravel/installer
RUN composer global require laravel/valet

#install vue-cli
RUN npm i -g @vue/cli


#copy apache run script
COPY ./run_script /usr/local/bin/run

RUN chmod +x /usr/local/bin/run

EXPOSE 8081
EXPOSE 80
EXPOSE 443
CMD ["/usr/local/bin/run"]