FROM ruby

LABEL maintainer="lrorscha@student.21-school.ru"

RUN apt update && apt install -y nodejs yarn && gem install 'rails:5.2.1' 'sqlite3:1.4.1' 'ffi:1.11.3' 'puma:3.12.1' && rails new /opt/app
EXPOSE 3000

ONBUILD WORKDIR /opt/app
ONBUILD RUN bundle install && rake db:migrate

#docker build -t ft-rails:on-build .
