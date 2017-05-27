# Django Cms Dockerfile
FROM ubuntu:14.04
MAINTAINER Rafał bluszcz Zawadzki <bluszcz@bluszcz.net>
RUN echo 'debconf debconf/frontend select Noninteractive' | debconf-set-selections
RUN apt-get update
RUN apt-get upgrade -y
RUN apt-get install python3.4-dev \ 
	wget -y \
	sqlite3 \
	python3-pip \
	python3-virtualenv \
	ssh \
	libpq-dev \
	libgdal1-dev \
	libgdal-dev
RUN apt-get build-dep pillow -y
RUN locale-gen en_US.UTF-8
ENV LANG en_US.UTF-8  
ENV LANGUAGE en_US:en  
ENV LC_ALL en_US.UTF-8
