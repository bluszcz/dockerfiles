# Django Cms Dockerfile
FROM ubuntu:18.04
MAINTAINER Rafał bluszcz Zawadzki <bluszcz@bluszcz.net>
RUN cat /etc/apt/sources.list
RUN sed -Ei 's/^# deb-src /deb-src /' /etc/apt/sources.list
RUN cat /etc/apt/sources.list
RUN echo 'debconf debconf/frontend select Noninteractive' | debconf-set-selections
RUN apt update
RUN apt-get upgrade -y
RUN apt-get install python3.6-dev \ 
	wget -y \
	sqlite3 \
	locales \
	python3-pip \
	ssh \
	libpq-dev \
	libgdal-dev
RUN apt-get build-dep pillow -y
RUN apt-get install sloccount -y
RUN apt-get install curl -y
RUN apt-get install postgresql-client -y
RUN pip3 install virtualenv
RUN locale-gen en_US.UTF-8
ENV LANG en_US.UTF-8  
ENV LANGUAGE en_US:en  
ENV LC_ALL en_US.UTF-8
