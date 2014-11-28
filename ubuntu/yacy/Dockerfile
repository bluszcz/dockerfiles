# Yacy Web Search by the People, for the People - Dockerfile 
FROM ubuntu:14.04
MAINTAINER Rafał bluszcz Zawadzki <bluszcz@bluszcz.net>
RUN echo 'debconf debconf/frontend select Noninteractive' | debconf-set-selections
RUN apt-get update
RUN apt-get upgrade -y
RUN apt-get install openjdk-7-jdk \
	wget -y
RUN useradd yacy
RUN mkdir -p /home/yacy/
RUN chown yacy /home/yacy -R
USER yacy
RUN wget http://www.yacy.net/release/yacy_v1.80_20140916_9000.tar.gz -O /home/yacy/yacy.tar.gz
RUN cd /home/yacy && tar zxvf yacy.tar.gz
RUN ls
USER root
RUN apt-get clean
RUN echo 'debconf debconf/frontend select Dialog' | debconf-set-selections
EXPOSE 8090
CMD sudo -u yacy /home/yacy/yacy/startYACY.sh -d
