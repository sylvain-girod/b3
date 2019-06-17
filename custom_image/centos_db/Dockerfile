FROM mysql

# Environment variables
ENV MYSQL_ROOT_PASSWORD 1234
ENV MYSQL_USER user
ENV MYSQL_PASSWORD 1234
ENV MYSQL_DATABSE wordpress

# Allows you to change the value of "max_allowed_packet"
#ADD ["mysqlconf/gatewaymy.cnf", "/etc/mysql/conf.d/conf_mysql.cnf"]

# Create Database
RUN    mkdir /usr/sql
RUN    chmod 644 /usr/sql

#ADD ["sql/sources.sql", "/usr/sql/sources.sql"]

RUN /etc/init.d/mysql start
RUN mysql -u root -p${MYSQL_ROOT_PASSWORD} -e "CREATE DATABASE lba"
RUN mysql -u root -p${MYSQL_ROOT_PASSWORD} -D lba < /usr/sql/sources.sql
RUN rm -rd /usr/sql

