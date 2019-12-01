#4. Docker can be useful to test an application that’s still being developed without polluting your libraries. You will have to design a Dockerfile that gets the development
#version of Gitlab - Community Edition installs it with all the dependencies and the necessary configurations, and launches the application, all as it builds. The container will be
#deemed valid if you can access the web client, create users and interact via GIT with this container (HTTPS and SSH).

FROM ubuntu

LABEL maintainer="lrorscha@student.21-school.ru"

EXPOSE 80 443 22

RUN apt update && apt install -y curl openssh-server tzdata ca-certificates && curl https://packages.gitlab.com/install/repositories/gitlab/gitlab-ce/script.deb.sh | bash
RUN apt install -y gitlab-ce

ENV gitlabRb="/opt/gitlab/gitlab.rb"

RUN mkdir -p /etc/gitlab/ssl && chmod 700 /etc/gitlab/ssl && sed -i -e "s/RANDFILE/#RANDFILE/" /etc/ssl/openssl.cnf && openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout /etc/gitlab/ssl/gitlab.example.com.key -out /etc/gitlab/ssl/gitlab.example.com.crt -subj /CN=gitlab.example.com && cat $gitlabRb | grep "external_url 'http://gitlab.example.com'" | sed -i "s/http/https/" && cat $gitlabRb

ENV gitlabRun="/opt/gitlab/embedded/bin/runsvdir-start"
ENV gitlabReconf="gitlab-ctl reconfigure"

ENTRYPOINT ($gitlabRun &) && $gitlabReconf && service ssh start && tail -f /dev/null

## RUN CONTAINER
# docker run --name gitlab -p 8081:80 -p 8443:443 -p 8022:22 -d  --privileged gitlab-ce

## HTTPS
# GIT_SSL_NO_VERIFY=true [git command] 

## SSH
### CONNECT ONLY WITH SSH KEY
### FIRST STEP - ADD SSH KEY TO GITLAB PROFILE
# GIT_SSH_COMMAND='ssh -i ~/.ssh/[key] -p 8022' [git command]
