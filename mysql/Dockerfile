FROM ssh
MAINTAINER danny <danny@kray.jp>

# mysql
RUN rpm -ivh http://dev.mysql.com/get/mysql-community-release-el6-5.noarch.rpm
RUN yum install -y mysql-community-server
RUN echo "NETWORKING=yes" >/etc/sysconfig/network
RUN /etc/init.d/mysqld start
ADD ./etc/supervisord.d/mysqld.ini /etc/supervisord.d/mysqld.ini
RUN mysql -u root -e "GRANT ALL PRIVILEGES ON *.* TO root@'172.17.0.%' WITH GRANT OPTION;"
