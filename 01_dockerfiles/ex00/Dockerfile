#1. From an alpine image you’ll add to your container your favorite text editor, vim or
#emacs, that will launch along with your container.

FROM alpine
LABEL maintainer="lrorscha@student.21-school.ru"

RUN apk add vim
ENTRYPOINT vim

#docker run --name vim -it vim
