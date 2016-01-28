FROM debian:jessie
MAINTAINER kakilangit <theguywhodrinkscoffeeandcodes@gmail.com>

ENV DEBIAN_FRONTEND noninteractive

RUN apt-get update && apt-get install -y wget \
  && printf "deb http://packages.dotdeb.org jessie all \ndeb-src http://packages.dotdeb.org jessie all " >> /etc/apt/sources.list \
  && wget https://www.dotdeb.org/dotdeb.gpg \
  && apt-key add dotdeb.gpg

RUN apt-get update && apt-get install -y \
  php7.0-common \
  php7.0-curl \
  php7.0-gd \
  php7.0-json \
  php7.0-tidy \
  php7.0-fpm \
  php7.0-opcache \
  php7.0-mysql \
  php7.0-dev \
  php7.0-cli \
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
  && apt-get autoremove -y \
  && apt-get autoclean \
  && apt-get clean \
  && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

CMD ["php-fpm7.0"]

EXPOSE 9000
