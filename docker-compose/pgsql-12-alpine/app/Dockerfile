FROM postgres:12.3-alpine

RUN apk update
RUN apk add openrc
RUN apk add nano
RUN echo "Asia/Jakarta" > /etc/timezone
RUN cp /usr/share/zoneinfo/Asia/Jakarta /etc/localtime
RUN export EDITOR=/usr/bin/nano
RUN /usr/sbin/crond enable
RUN /usr/sbin/crond start
