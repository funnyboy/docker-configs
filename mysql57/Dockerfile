FROM mysql:5.7

MAINTAINER Dmitry Zaiets "funnyboy1190@gmail.com"

ENV MYSQL_ROOT_PASSWORD 12345
ENV MYSQL_PASSWORD 12345
ENV MYSQL_DATABASE test

# this need to stay the same for script to work
ENV MYSQL_USER mysql

COPY ./localdb-run.sh /
RUN chmod 755 /localdb-run.sh

ENTRYPOINT ["/localdb-run.sh"]
