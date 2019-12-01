#2. From a debian image you will add the appropriate sources to create a TeamSpeak
#server, that will launch along with your container. It will be deemed valid if at least
#one user can connect to it and engage in a normal discussion (no far-fetched setup), so
#be sure to create your Dockerfile with the right options. Your program should get the
#sources when it builds, they cannot be in your repository

FROM debian

LABEL maintainer="lrorscha@student.21-school.ru"

EXPOSE 9987/UDP 30033 10011

ENV TS3SERVER_LICENSE=accept
RUN apt update && apt install -y bzip2 wget && \
wget https://files.teamspeak-services.com/releases/server/3.10.2/teamspeak3-server_linux_amd64-3.10.2.tar.bz2 && \
tar xfv teamspeak3-server_linux_amd64-3.10.2.tar.bz2 && rm teamspeak3-server_linux_amd64-3.10.2.tar.bz2

WORKDIR teamspeak3-server_linux_amd64

ENTRYPOINT ./ts3server_minimal_runscript.sh

#docker run --name ts3 -p 30033:30033 -p 10011:10011 -p 9987:9987/udp ts3
