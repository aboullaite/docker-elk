FROM nginx
MAINTAINER Aboullaite Mohammed
ENV DEBIAN_FRONTEND noninteractive

### install Filebeat

ENV FILEBEAT_VERSION 5.2.1

RUN apt-get update -qq \
 && apt-get install -qqy curl \
 && apt-get clean

RUN curl -L -O https://artifacts.elastic.co/downloads/beats/filebeat/filebeat-${FILEBEAT_VERSION}-amd64.deb \
 && dpkg -i filebeat-${FILEBEAT_VERSION}-amd64.deb \
 && rm filebeat-${FILEBEAT_VERSION}-amd64.deb


###############################################################################
#                                CONFIGURATION
###############################################################################

### tweak nginx image set-up

# remove log symlinks
RUN rm /var/log/nginx/access.log /var/log/nginx/error.log


### configure Filebeat

# config file
ADD filebeat.yml /etc/filebeat/filebeat.yml

###############################################################################
#                                    DATA
###############################################################################

### add dummy HTML file

COPY html /usr/share/nginx/html

###############################################################################
#                                    START
###############################################################################

ADD ./start.sh /usr/local/bin/start.sh
RUN chmod +x /usr/local/bin/start.sh
CMD [ "/usr/local/bin/start.sh" ]
