FROM ubuntu:trusty
MAINTAINER kakilangit <theguywhodrinkscoffeeandcodes@gmail.com>

ENV DEBIAN_FRONTEND noninteractive

RUN apt-get update && apt-get upgrade -y &&\
	apt-get install -y php5-cli php5-common php5-curl php5-dev php5-gd php5-json php5-tidy php5-xsl php5-apcu php5-fpm php5-geoip php5-imagick php5-intl php5-mcrypt php5-memcache php5-memcached php5-mongo php5-mysqlnd memcached

ADD config/php.ini /etc/php5/fpm/php.ini
ADD config/php-fpm.conf /etc/php5/fpm/php-fpm.conf
ADD config/www.conf /etc/php5/fpm/pool.d/www.conf

RUN rm -rf /etc/php5/cli/php.ini && \
    ln -s /etc/php5/fpm/php.ini /etc/php5/cli/php.ini

RUN cd /tmp && \
    php -r "readfile('https://getcomposer.org/installer');" | php && \
    mv composer.phar /usr/local/bin/composer
    
RUN apt-get autoremove && \
    apt-get autoclean && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

CMD ["php5-fpm"]

EXPOSE 9000