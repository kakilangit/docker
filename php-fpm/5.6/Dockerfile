FROM ubuntu:trusty
MAINTAINER kakilangit <theguywhodrinkscoffeeandcodes@gmail.com>

ENV DEBIAN_FRONTEND noninteractive

#https://secure.php.net/downloads.php
RUN apt-get update && apt-get install -y language-pack-en-base software-properties-common && LC_ALL=en_US.UTF-8 add-apt-repository ppa:ondrej/php \
  && apt-get update && apt-get install -y \
    php5.6-bz2 \
    php5.6-bcmath \
    php5.6-cgi \
    php5.6-cli \
    php5.6-common \
    php5.6-curl \
    php5.6-dev \
    php5.6-enchant \
    php5.6-fpm \
    php5.6-gd \
    php5.6-gmp \
    php5.6-intl \
    php5.6-json \
    php5.6-mcrypt \
    php5.6-mbstring \
    php5.6-mysql \
    php5.6-opcache \
    php5.6-pgsql \
    php5.6-phpdbg \
    php5.6-readline \
    php5.6-recode \
    php5.6-sqlite3 \
    php5.6-xmlrpc \
    php5.6-zip \
    php5.6-tidy \
    php-apcu  \
    php-imagick \
    php-memcached \
    php-mongodb \
    memcached \
    optipng \
    gifsicle \
    libjpeg-turbo-progs

COPY config/php.ini /etc/php/5.6/fpm/php.ini
COPY config/php-fpm.conf /etc/php/5.6/fpm/php-fpm.conf
COPY config/www.conf /etc/php/5.6/fpm/pool.d/www.conf

RUN rm -rf /etc/php/5.6/cli/php.ini \
  && ln -s /etc/php/5.6/fpm/php.ini /etc/php/5.6/cli/php.ini \
  && cd /tmp \
  && php -r "readfile('https://getcomposer.org/installer');" | php \
  && mv composer.phar /usr/local/bin/composer \
  && apt-get remove -y software-properties-common \
  && apt-get autoremove -y \
  && apt-get autoclean \
  && apt-get clean \
  && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

CMD ["php5-fpm"]

EXPOSE 9000
