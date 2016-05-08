FROM ubuntu:trusty
MAINTAINER kakilangit <theguywhodrinkscoffeeandcodes@gmail.com>

ENV DEBIAN_FRONTEND noninteractive

# https://secure.php.net/downloads.php
RUN apt-get update && apt-get install -y language-pack-en-base software-properties-common && LC_ALL=en_US.UTF-8 add-apt-repository ppa:ondrej/php \
  && apt-get update && apt-get install -y \
  php7.0-bz2 \
  php7.0-bcmath \
  php7.0-cgi \
  php7.0-common \
  php7.0-cli \
  php7.0-curl \
  php7.0-dev \
  php7.0-enchant \
  php7.0-fpm \
  php7.0-gd \
  php7.0-gmp \
  php7.0-intl \
  php7.0-json \
  php7.0-mcrypt \
  php7.0-mysql \
  php7.0-mbstring \
  php7.0-opcache \
  php7.0-pgsql \
  php7.0-phpdbg \
  php7.0-readline \
  php7.0-recode \
  php7.0-sqlite3 \
  php7.0-tidy \
  php7.0-xsl \
  php7.0-xml \
  php7.0-xmlrpc \
  php7.0-zip \
  php-apcu  \
  php-imagick \
  php-memcached \
  php-mongodb \
  memcached \
  optipng \
  gifsicle \
  libjpeg-turbo-progs

ADD config/php.ini /etc/php/7.0/fpm/php.ini
ADD config/php-fpm.conf /etc/php/7.0/fpm/php-fpm.conf
ADD config/www.conf /etc/php/7.0/fpm/pool.d/www.conf

RUN rm -rf /etc/php/7.0/cli/php.ini \
  && ln -s /etc/php/7.0/fpm/php.ini /etc/php/7.0/cli/php.ini \
  && cd /tmp \
  && php -r "readfile('https://getcomposer.org/installer');" | php \
  && mv composer.phar /usr/local/bin/composer \
  && apt-get remove -y software-properties-common \
  && apt-get autoremove -y \
  && apt-get autoclean \
  && apt-get clean \
  && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

CMD ["php-fpm7.0"]

EXPOSE 9000
