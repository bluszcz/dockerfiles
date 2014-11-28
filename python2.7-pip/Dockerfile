# Ubuntu Trusty Dockerfile 
# Customized python pip installation due to the bugs in Ubuntu
FROM ubuntu:14.04
MAINTAINER Rafał bluszcz Zawadzki <bluszcz@bluszcz.net>
RUN cd /tmp/
RUN echo 'debconf debconf/frontend select Noninteractive' | debconf-set-selections
RUN apt-get update
RUN apt-get upgrade -y
# pip seems be messed up in Ubuntu Trusty source:
# https://bugs.launchpad.net/ubuntu/+source/python-pip/+bug/1306991
# https://bugs.launchpad.net/ubuntu/trusty/+source/python-pip/+bug/1308714
RUN apt-get install python2.7-dev wget -y 
RUN apt-get remove python-pip
RUN wget https://bootstrap.pypa.io/get-pip.py
RUN /usr/bin/python2.7 get-pip.py
RUN apt-get clean
RUN echo 'debconf debconf/frontend select Dialog' | debconf-set-selections
