FROM debian

RUN apt-get update && apt-get upgrade
RUN apt install -y wget default-jre
RUN adduser hye --home /home/hye --disabled-password --uid 1002 --disabled-login
#The EULA line will be removed in production, Ararat maintains the capability to show a popup when EULA acceptance is required.
RUN echo "eula=true" > /home/hye/eula.txt
#Will be configured to have version entry, and will automatically retrieve latest built in future builds.
RUN cd /home/hye && wget -O server.jar https://papermc.io/api/v2/projects/paper/versions/1.16.5/builds/786/downloads/paper-1.16.5-786.jar
RUN cd /home/hye && wget -O server.properties https://raw.githubusercontent.com/Hye-Organization/magma/main/minecraft/paper/1.16/server.properties

USER hye
ENV USER=hye HOME=/home/hye
WORKDIR /home/hye
ENTRYPOINT [ "/usr/bin/java" , "-jar", "/home/hye/server.jar"]