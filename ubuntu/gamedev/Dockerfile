# Godot CI Dockerfile
FROM bluszcz/godot
MAINTAINER Rafał bluszcz Zawadzki <bluszcz@bluszcz.net>
RUN echo 'debconf debconf/frontend select Noninteractive' | debconf-set-selections

RUN apt-get update \ 
    && apt-get upgrade -y \ 
    && apt-get install -y -qq libsfml-dev build-essential games-c++-dev



RUN echo 'debconf debconf/frontend select Dialog' | debconf-set-selections
