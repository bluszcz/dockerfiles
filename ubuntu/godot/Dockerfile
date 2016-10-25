# Godot CI Dockerfile
FROM ubuntu:16.04
MAINTAINER Rafał bluszcz Zawadzki <bluszcz@bluszcz.net>
RUN echo 'debconf debconf/frontend select Noninteractive' | debconf-set-selections
RUN apt-get update \ 
    && apt-get upgrade -y \ 
    && apt-get install -y -qq sqlite3 libsqlite3-dev nodejs wget unzip \
    && mkdir -p /opt/
RUN cd /opt
  - wget https://downloads.tuxfamily.org/godotengine/2.1/Godot_v2.1-stable_x11.64.zip
  - unzip Godot_v2.1-stable_x11.64.zip
RUN locale-gen en_US.UTF-8
ENV LANG en_US.UTF-8  
ENV LANGUAGE en_US:en  
ENV LC_ALL en_US.UTF-8
USER root
RUN apt-get clean
RUN echo 'debconf debconf/frontend select Dialog' | debconf-set-selections
