FROM ubuntu:trusty
MAINTAINER kakilangit <theguywhodrinkscoffeeandcodes@gmail.com>

ENV DEBIAN_FRONTEND noninteractive

RUN printf "deb http://ppa.launchpad.net/ondrej/php/ubuntu trusty main \ndeb-src http://ppa.launchpad.net/ondrej/php/ubuntu trusty main " >> /etc/apt/sources.list \
  && apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 4F4EA0AAE5267A6C \
  && apt-get update && apt-get install -y \
    php5.6-bz2 \
    php5.6-cli \
    php5.6-common \
    php5.6-curl \
    php5.6-dbg \
    php5.6-dev \
    php5.6-fpm \
    php5.6-gd \
    php5.6-intl \
    php5.6-json \
    php5.6-mcrypt \
    php5.6-mysql \
    php5.6-opcache \
    php5.6-pgsql \
    php5.6-readline \
    php5.6-tidy \
    php5.6-xsl \
    php-apcu  \
    php-imagick \
    php-memcached \
    php-mongodb \
    memcached \
    optipng \
    gifsicle \
    libjpeg-turbo-progs

ADD config/php.ini /etc/php5/fpm/php.ini
ADD config/php-fpm.conf /etc/php5/fpm/php-fpm.conf
ADD config/www.conf /etc/php5/fpm/pool.d/www.conf

RUN rm -rf /etc/php5/cli/php.ini \
  && ln -s /etc/php5/fpm/php.ini /etc/php5/cli/php.ini \
  && cd /tmp \
  && php -r "readfile('https://getcomposer.org/installer');" | php \
  && mv composer.phar /usr/local/bin/composer \
  && apt-get autoremove -y \
  && apt-get autoclean \
  && apt-get clean \
  && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

CMD ["php5-fpm"]

EXPOSE 9000
