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
					php5.6 \
					php5.6-cli \
					php5.6-fpm \
					php5.6-common \
					php5.6-curl \
					php5.6-gd \
					php5.6-mysql \
					php5.6-soap \
					php5.6-xml \
					php5.6-zip \
					php5.6-mbstring \
					php5.6-mcrypt \
					php5.6-intl \
					libapache2-mod-php5.6

RUN curl -sS https://getcomposer.org/installer -o composer-setup.php

RUN php composer-setup.php --install-dir=/bin --filename=composer

COPY ./apache_default_env /etc/apache2/sites-available/000-default.conf
COPY ./run_script /usr/local/bin/run

RUN chmod +x /usr/local/bin/run
RUN a2enmod rewrite

EXPOSE 80
CMD ["/usr/local/bin/run"]