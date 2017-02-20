FROM openjdk:8

MAINTAINER Aboullaite Mohammed
ENV DEBIAN_FRONTEND noninteractive

ENV LOGSTASH_VERSION 5.2.1
# Add lsuser to avoid starting logstash as the root user.
RUN useradd -d /home/lsuser -m lsuser
WORKDIR /home/lsuser

# Install logstash
RUN \
wget https://artifacts.elastic.co/downloads/logstash/logstash-${LOGSTASH_VERSION}.tar.gz && \
tar xvzf logstash-${LOGSTASH_VERSION}.tar.gz && \
rm -f logstash-${LOGSTASH_VERSION}.tar.gz && \
chown -R lsuser:lsuser logstash-${LOGSTASH_VERSION}


# logstash.conf and Dockerfile are on same location
ADD logstash.conf /home/lsuser
CMD logstash-${LOGSTASH_VERSION}/bin/logstash -f logstash.conf --verbose
