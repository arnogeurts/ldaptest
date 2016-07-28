FROM ubuntu:latest

MAINTAINER Arno Geurts

ENV HOME /root
ENV DEBIAN_FRONTEND noninteractive

RUN apt-get -q update && apt-get install -y unixodbc odbc-postgresql slapd ldap-utils postgresql-client-9.5

ADD etc/odbc/odbc.ini /etc/odbc.ini
ADD etc/odbc/odbcinst.ini /etc/odbcinst.ini
ADD etc/slapd/slapd.conf /etc/ldap/slapd.conf

ADD scripts/start-ldap.sh /usr/bin/start-ldap.sh
RUN chmod u+x /usr/bin/start-ldap.sh

RUN mkdir -p /usr/local/var/

RUN apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* 

CMD "/usr/bin/start-ldap.sh"
