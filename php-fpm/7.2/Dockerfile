FROM debian:stretch
MAINTAINER kakilangit <theguywhodrinkscoffeeandcodes@gmail.com>

ENV DEBIAN_FRONTEND noninteractive

# https://secure.php.net/downloads.php
RUN apt-get update && apt-get install -y dirmngr wget apt-transport-https lsb-release ca-certificates && wget -O /etc/apt/trusted.gpg.d/php.gpg https://packages.sury.org/php/apt.gpg
RUN echo "deb https://packages.sury.org/php/ $(lsb_release -sc) main" > /etc/apt/sources.list.d/php.list
RUN apt-get update
RUN apt-get install -y \
  php7.2-bz2 \
  php7.2-bcmath \
  php7.2-cgi \
  php7.2-common \
  php7.2-cli \
  php7.2-curl \
  php7.2-dev \
  php7.2-enchant \
  php7.2-fpm \
  php7.2-gd \
  php7.2-gmp \
  php7.2-intl \
  php7.2-json \
  php7.2-mysql \
  php7.2-mbstring \
  php7.2-opcache \
  php7.2-pgsql \
  php7.2-phpdbg \
  php7.2-readline \
  php7.2-recode \
  php7.2-sqlite3 \
  php7.2-tidy \
  php7.2-xsl \
  php7.2-xml \
  php7.2-xmlrpc \
  php7.2-zip
RUN apt-get install -y \
  memcached \
  optipng \
  gifsicle \
  libjpeg-turbo-progs

COPY config/php.ini /etc/php/7.2/fpm/php.ini
COPY config/php-fpm.conf /etc/php/7.2/fpm/php-fpm.conf
COPY config/www.conf /etc/php/7.2/fpm/pool.d/www.conf

RUN rm -rf /etc/php/7.2/cli/php.ini \
  && ln -s /etc/php/7.2/fpm/php.ini /etc/php/7.2/cli/php.ini \
  && cd /tmp \
  && php -r "readfile('https://getcomposer.org/installer');" | php \
  && mv composer.phar /usr/local/bin/composer \
  && apt-get autoremove -y \
  && apt-get autoclean \
  && apt-get clean \
  && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

CMD ["php-fpm7.2"]

EXPOSE 9000
