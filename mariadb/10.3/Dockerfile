FROM debian:stretch
MAINTAINER kakilangit <theguywhodrinkscoffeeandcodes@gmail.com>

# https://downloads.mariadb.org/
ENV DEBIAN_FRONTEND noninteractive
ENV TERM dumb

RUN apt-get update && apt-get install -y software-properties-common dirmngr \
	&& apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 0xF1656F24C74CD1D8 \
	&& add-apt-repository 'deb [arch=amd64,i386,ppc64el] http://mirrors.n-ix.net/mariadb/repo/10.3/debian stretch main'

RUN groupadd -r mysql && useradd -r -g mysql mysql \
	&& apt-get update && apt-get install -y \
	mariadb-server \
	pwgen \
	&& apt-get autoremove -y \
  && apt-get autoclean \
  && apt-get clean \
	&& rm -rf /var/lib/mysql/* /var/lib/apt/lists/*

COPY config/my.cnf /etc/mysql/my.cnf
COPY config/create_mariadb_admin_user.sh /create_mariadb_admin_user.sh
COPY config/run.sh /run.sh
RUN chmod 775 /*.sh

VOLUME  ["/etc/mysql", "/var/lib/mysql"]

EXPOSE 3306
CMD ["/run.sh"]
