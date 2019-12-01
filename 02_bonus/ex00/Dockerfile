FROM debian

LABEL maintainer="lrorscha@student.21-school.ru"

EXPOSE 25565

RUN apt update && apt install -y git default-jdk wget screen
RUN mkdir -p /opt/MC_Serv

WORKDIR /opt/MC_Serv

RUN wget https://hub.spigotmc.org/jenkins/job/BuildTools/lastSuccessfulBuild/artifact/target/BuildTools.jar
RUN java -Xmx1024M -jar BuildTools.jar --rev 1.14.4
RUN java -Xms1024M -Xmx2048M -jar spigot-1.14.4.jar nogui && sed -i -e "s/false/true/" eula.txt

ENTRYPOINT screen -dmS mc_serv java -Xms1024M -Xmx2048M -jar spigot-1.14.4.jar nogui && tail -f /dev/null
