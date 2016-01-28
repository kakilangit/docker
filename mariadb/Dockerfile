FROM debian:jessie
MAINTAINER kakilangit <theguywhodrinkscoffeeandcodes@gmail.com>

ENV DEBIAN_FRONTEND noninteractive
ENV TERM dumb

RUN printf "deb http://mariadb.biz.net.id/repo/10.1/ubuntu trusty main" >> /etc/apt/sources.list \
	&& apt-key adv --recv-keys --keyserver hkp://keyserver.ubuntu.com:80 0xcbcb082a1bb943db \
	&& apt-get update && apt-get install -y \
	mariadb-server \
	mariadb-oqgraph-engine-10.1 \
	pwgen \
	&& apt-get autoremove -y \
  && apt-get autoclean \
  && apt-get clean \
	&& rm -rf /var/lib/mysql/* /var/lib/apt/lists/*

ADD config/my.cnf /etc/mysql/my.cnf
ADD config/create_mariadb_admin_user.sh /create_mariadb_admin_user.sh
ADD config/run.sh /run.sh
RUN chmod 775 /*.sh

VOLUME  ["/etc/mysql", "/var/lib/mysql"]

EXPOSE 3306
CMD ["/run.sh"]
