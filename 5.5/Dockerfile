FROM oraclelinux:latest

## -- The environment variables set using ENV will persist when a container
## -- is run from the resulting image. -- ##

ENV PACKAGE_URL https://repo.mysql.com/yum/mysql-5.5-community/docker/x86_64/mysql-community-server-minimal-5.5.43-2.el7.x86_64.rpm

# Install server
RUN rpmkeys --import http://repo.mysql.com/RPM-GPG-KEY-mysql \
  && yum install -y $PACKAGE_URL \
  && rm -rf /var/cache/yum/*

VOLUME /var/lib/mysql

COPY docker-entrypoint.sh /entrypoint.sh
ENTRYPOINT ["/entrypoint.sh"]

EXPOSE 3306
CMD ["mysqld"]

