FROM alpine

LABEL maintainer="lrorscha@student.21-school.ru"

RUN apk add build-base git && git clone git://github.com/klange/nyancat.git /opt/nyancat

WORKDIR /opt/nyancat/src

RUN make

ENTRYPOINT ./nyancat
