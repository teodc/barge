FROM mysql:latest

EXPOSE 3306

RUN ln -snf /usr/share/zoneinfo/UTC /etc/localtime \
    && echo UTC > /etc/timezone \
    && chown -R mysql:root /var/lib/mysql/

COPY my.cnf /etc/mysql/conf.d/my.cnf

WORKDIR /etc/mysql

ENTRYPOINT ["mysqld"]
