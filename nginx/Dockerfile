FROM ruby
MAINTAINER danny <danny@kray.jp>

# mysql-client
RUN rpm -ivh http://dev.mysql.com/get/mysql-community-release-el6-5.noarch.rpm
RUN yum install -y mysql-community-client mysql-community-devel

# nginx
RUN yum -y install nginx
ADD ./etc/supervisord.d/nginx.ini /etc/supervisord.d/nginx.ini

RUN mkdir -p /var/www/vhosts/appserver/shared/log
RUN mkdir -p /var/www/vhosts/appserver/shared/config
ADD ./database.yml /var/www/vhosts/appserver/shared/config/database.yml
RUN chown -R app:app /var/www/vhosts/appserver
RUN mkdir -p /etc/nginx/vhosts.d
RUN mkdir -p /etc/nginx/htpasswd.d

ADD ./etc/nginx/nginx.conf /etc/nginx/nginx.conf
RUN mkdir -p /etc/nginx/vhosts.d/common
ADD ./etc/nginx/vhosts.d/common/proxy.conf /etc/nginx/vhosts.d/common/proxy.conf
ADD ./etc/nginx/vhosts.d/appserver.conf /etc/nginx/vhosts.d/appserver.conf
