FROM centos

RUN yum install -y tar postgresql-devel

ENV POSTGREST_VERSION 0.3.0.2
ENV DBHOST localhost
ENV DBPORT 5432
ENV DBNAME my_db
ENV DBUSER postgres
ENV DBPASS foobar
ENV V1SCHEMA public

RUN curl -L http://bin.begriffs.com/dbapi/heroku/postgrest-${POSTGREST_VERSION}.tar.xz \
    | tar -xJO > /usr/local/bin/postgrest \
    && chmod u+x /usr/local/bin/postgrest

CMD postgrest  postgres://${DBUSER}:${DBPASS}@${DBHOST}:${DBPORT}/${DBNAME} \
               --pool 200 \
               --anonymous postgres \
               --port 3000 \
               --schema ${V1SCHEMA}

EXPOSE 3000
