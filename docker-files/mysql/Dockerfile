FROM mysql:8.0

EXPOSE 3306

WORKDIR /etc/mysql

RUN ln -snf /usr/share/zoneinfo/UTC /etc/localtime \
    && echo UTC > /etc/timezone \
    && chown -R mysql:root /var/lib/mysql/

COPY my.cnf /etc/mysql/conf.d/

CMD ["mysqld"]
