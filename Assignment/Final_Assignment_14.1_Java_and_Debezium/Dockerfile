FROM mysql:8.0

ENV MYSQL_DATABASE=employeedb \
    MYSQL_ROOT_PASSWORD=MyNewPass

COPY employee.sql /docker-entrypoint-initdb.d/

CMD ["mysqld", "--server-id=1", "--log-bin=mysql-bin", "--binlog-format=ROW", "--binlog-row-image=FULL"]

EXPOSE 3306