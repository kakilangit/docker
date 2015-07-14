FROM ubuntu:trusty
MAINTAINER kakilangit <theguywhodrinkscoffeeandcodes@gmail.com>

ENV DEBIAN_FRONTEND noninteractive
ENV TERM dumb

#Disabling Transparent HugePage Support for TokuDB on your host
#https://mariadb.com/kb/en/mariadb/enabling-tokudb/#check-for-transparent-hugepage-support-on-linux

RUN apt-get install -y software-properties-common && \
	apt-key adv --recv-keys --keyserver hkp://keyserver.ubuntu.com:80 0xcbcb082a1bb943db && \
    add-apt-repository 'deb http://mariadb.biz.net.id/repo/10.1/ubuntu trusty main' && \
    apt-get update && apt-get upgrade -y &&\
	apt-get install -y mariadb-server mariadb-oqgraph-engine-10.1 pwgen && \
    rm -rf /var/lib/mysql/* && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

ADD config/my.cnf /etc/mysql/my.cnf
ADD config/create_mariadb_admin_user.sh /create_mariadb_admin_user.sh
ADD config/run.sh /run.sh
RUN chmod 775 /*.sh

VOLUME  ["/etc/mysql", "/var/lib/mysql"]

EXPOSE 3306
CMD ["/run.sh"]