# Taken from https://github.com/Homegear/Homegear-Docker/blob/master/rpi-stable/Dockerfile
FROM resin/rpi-raspbian:stretch
MAINTAINER Jan Schulz-Hofen <hassio@0.jan.sh>

RUN apt-get update && apt-get -y install apt-transport-https wget ca-certificates apt-utils gnupg
RUN wget https://homegear.eu/packages/Release.key && apt-key add Release.key && rm Release.key
RUN echo 'deb https://homegear.eu/packages/Raspbian/ stretch/' >> /etc/apt/sources.list.d/homegear.list
RUN apt-get update && apt-get -y install ntp
RUN apt-get -y install tzdata 
RUN apt-get -y install homegear 
RUN apt-get -y install homegear-nodes-core 
RUN apt-get -y install homegear-nodes-extra 
# RUN apt-get -y install homegear-homematicbidcos 
# RUN apt-get -y install homegear-homematicwired 
# RUN apt-get -y install homegear-insteon 
RUN apt-get -y install homegear-max 
# RUN apt-get -y install homegear-philipshue 
# RUN apt-get -y install homegear-sonos 
# RUN apt-get -y install homegear-kodi 
# RUN apt-get -y install homegear-ipcam 
# RUN apt-get -y install homegear-beckhoff 
# RUN apt-get -y install homegear-knx 
# RUN apt-get -y install homegear-enocean 
# RUN apt-get -y install homegear-intertechno 
# RUN apt-get -y install homegear-influxdb 
RUN apt-get -y install vim 
RUN apt-get -y install less 
RUN apt-get -y install htop
RUN rm -f /etc/homegear/dh1024.pem
RUN rm -f /etc/homegear/homegear.crt
RUN rm -f /etc/homegear/homegear.key
RUN cp -R /etc/homegear /etc/homegear.config
RUN cp -R /var/lib/homegear /var/lib/homegear.data

# Inspired by Dockerfile from visevision
RUN apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

COPY start.sh /start.sh
RUN chmod +x /start.sh
USER root
CMD /start.sh

EXPOSE 2001
