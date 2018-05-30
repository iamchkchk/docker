FROM ubuntu:16.04

ENV APACHE_LOG_DIR="/var/log/apache2"

RUN apt-get update && apt-get install -y software-properties-common

RUN LC_ALL=C.UTF-8 add-apt-repository -y -u ppa:ondrej/php

RUN apt-get update && apt-get install -y \
					curl \
					cron \
					unzip \
					git \
					apache2 \
					php7.0 \
					php7.0-cli \
					php7.0-fpm \
					php7.0-common \
					php7.0-curl \
					php7.0-gd \
					php7.0-mysql \
					php7.0-soap \
					php7.0-xml \
					php7.0-zip \
					php7.0-mbstring \
					php7.0-mcrypt \
					php7.0-intl \
					libapache2-mod-php7.0

RUN curl -sS https://getcomposer.org/installer -o composer-setup.php

RUN php composer-setup.php --install-dir=/bin --filename=composer

COPY ./apache_default_env /etc/apache2/sites-available/000-default.conf
COPY ./run_script /usr/local/bin/run

RUN chmod +x /usr/local/bin/run
RUN a2enmod rewrite

EXPOSE 80
CMD ["/usr/local/bin/run"]