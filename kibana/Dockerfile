FROM openjdk:8

MAINTAINER Aboullaite Mohammed
ENV DEBIAN_FRONTEND noninteractive

ENV KIBANA_VERSION 5.2.1
# Add kbuser to avoid starting Kibana as the root user.
RUN useradd -d /home/kbuser -m kbuser
WORKDIR /home/kbuser

# Install Kibana
RUN \
wget https://artifacts.elastic.co/downloads/kibana/kibana-${KIBANA_VERSION}-linux-x86_64.tar.gz && \
tar xvzf kibana-${KIBANA_VERSION}-linux-x86_64.tar.gz && \
rm -f kibana-${KIBANA_VERSION}-linux-x86_64.tar.gz && \
chown -R kbuser:kbuser kibana-${KIBANA_VERSION}-linux-x86_64

# Kibana.yml and Dockerfile are on same location
ADD kibana.yml kibana-${KIBANA_VERSION}-linux-x86_64/config/kibana.yml
ENTRYPOINT kibana-${KIBANA_VERSION}-linux-x86_64/bin/kibana
