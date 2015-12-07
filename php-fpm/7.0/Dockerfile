FROM ubuntu:trusty
MAINTAINER kakilangit <theguywhodrinkscoffeeandcodes@gmail.com>

ENV DEBIAN_FRONTEND noninteractive

RUN echo "deb http://ppa.launchpad.net/ondrej/php-7.0/ubuntu trusty main \ndeb-src http://ppa.launchpad.net/ondrej/php-7.0/ubuntu trusty main " >> /etc/apt/sources.list
RUN apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 4F4EA0AAE5267A6C
RUN apt-get update && apt-get upgrade -y
RUN apt-get install -y php7.0-cli php7.0-common php7.0-curl php7.0-dev php7.0-gd php7.0-json php7.0-tidy php7.0-fpm php7.0-opcache php7.0-mysql
RUN apt-get install -y memcached optipng gifsicle libjpeg-progs

ADD config/php.ini /etc/php/7.0/fpm/php.ini
ADD config/php-fpm.conf /etc/php/7.0/fpm/php-fpm.conf
ADD config/www.conf /etc/php/7.0/fpm/pool.d/www.conf

RUN rm -rf /etc/php/7.0/cli/php.ini && \
    ln -s /etc/php/7.0/fpm/php.ini /etc/php/7.0/cli/php.ini

RUN cd /tmp && \
    php -r "readfile('https://getcomposer.org/installer');" | php && \
    mv composer.phar /usr/local/bin/composer

RUN apt-get autoremove -y && \
    apt-get autoclean && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

CMD ["php7.0-fpm"]

EXPOSE 9000
