# Godot CI Dockerfile
FROM ubuntu:16.04
MAINTAINER Rafał bluszcz Zawadzki <bluszcz@bluszcz.net>
RUN echo 'debconf debconf/frontend select Noninteractive' | debconf-set-selections
RUN apt-get update \ 
    && apt-get upgrade -y \ 
    && apt-get install -y -qq sqlite3 libsqlite3-dev nodejs wget unzip libx11-6 \
    && mkdir -p /opt/
RUN cd /opt \
    && wget https://downloads.tuxfamily.org/godotengine/2.1/Godot_v2.1-stable_x11.64.zip \
    && unzip Godot_v2.1-stable_x11.64.zip
RUN locale-gen en_US.UTF-8
ENV LANG en_US.UTF-8  
ENV LANGUAGE en_US:en  
ENV LC_ALL en_US.UTF-8
USER root
RUN apt-get install libxinerama1 -y
RUN apt-get install libxcursor1 -y
RUN apt-get install -y build-essential scons pkg-config libx11-dev libxcursor-dev libxinerama-dev \
    libgl1-mesa-dev libglu-dev libasound2-dev libpulse-dev libfreetype6-dev libssl-dev libudev-dev \
    libxrandr-dev
RUN apt-get clean
RUN echo 'debconf debconf/frontend select Dialog' | debconf-set-selections
CMD /opt/Godot_v2.1-stable_x11.64 --help
