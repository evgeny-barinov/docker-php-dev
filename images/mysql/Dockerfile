FROM mysql:latest
RUN echo "[mysqld]" >> /etc/mysql/my.cnf \
    && echo "sql_mode='ONLY_FULL_GROUP_BY,NO_ZERO_IN_DATE,NO_ZERO_DATE,ERROR_FOR_DIVISION_BY_ZERO,NO_AUTO_CREATE_USER,NO_ENGINE_SUBSTITUTION'" >> /etc/mysql/my.cnf