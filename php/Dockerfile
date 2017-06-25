FROM debian:latest

RUN apt-get update && apt-get install -y locales && rm -rf /var/lib/apt/lists/* \
    && localedef -i de_DE -c -f UTF-8 -A /usr/share/locale/locale.alias de_DE.UTF-8
ENV LANG de_DE.utf8

RUN echo 'deb http://packages.dotdeb.org jessie all' > /etc/apt/sources.list.d/dotdeb.list

RUN apt-get -qq update && apt-get install -y --force-yes screen \
	wget \
	unzip \
	curl \
	git \
	systemd \
	lsb-release \
	vim \
	apt-transport-https \
	nginx

RUN curl http://www.dotdeb.org/dotdeb.gpg | apt-key add -

RUN apt-get -qq update && apt-get install -y --force-yes php7.0 \
    php7.0-cli \
    php7.0-fpm \
    php7.0-curl \
    php7.0-gd \
    php7.0-geoip \
    php7.0-intl \
    php7.0-json \
    php7.0-mbstring \
    php7.0-mcrypt \
    php7.0-mysql \
    php7.0-opcache \
    php7.0-readline \
    php7.0-xml \
    php7.0-xsl \
    php7.0-zip


COPY assets/virtual_host /etc/nginx/sites-enabled/default
#COPY assets/index.html /var/www/html/index.html
#EXPOSE 81
#EXPOSE 22

STOPSIGNAL  SIGQUIT
CMD ["nginx", "-g", "daemon off;"] && ["php-fpm7.0", "-F"]

#&& ["/usr/sbin/sshd", "-D"]

#COPY startup/start.sh /
#ENTRYPOINT ["/start.sh"]
#
#FROM mysql:8.0
#ENV MYSQL_ROOT_PASSWORD=test1234
#ENV MYSQL_ROOT_HOST=%
#EXPOSE 3306
#CMD ["mysqld"]


#RUN echo 'deb http://repo.mysql.com/apt/debian/ jessie mysql-5.7' > /etc/apt/sources.list.d/mysql.list
#RUN apt-get install apt-transport-https
#RUN apt-key adv --keyserver pgp.mit.edu --recv-keys 5072E1F5
#RUN apt-get update && apt-get install -q -y mysql-community-client mysql-community-server

#RUN wget http://dev.mysql.com/get/mysql-apt-config_0.6.0-1_all.deb
#RUN dpkg -i mysql-apt-config_0.6.0-1_all.deb
#
#RUN echo "mysql-server mysql-server/root_password password root" | debconf-set-selections
#RUN echo "mysql-server mysql-server/root_password_again password root" | debconf-set-selections
#RUN apt-get -q -y install mysql-server
#

