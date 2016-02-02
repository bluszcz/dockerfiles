# Ubuntu Trusty Dockerfile 
FROM ubuntu:14.04.3
MAINTAINER Rafał bluszcz Zawadzki <bluszcz@bluszcz.net>
RUN echo 'debconf debconf/frontend select Noninteractive' | debconf-set-selections
RUN apt-get update
RUN apt-get upgrade -y
RUN apt-get clean
RUN useradd -ms /bin/bash jenkins
RUN apt-get install openssh-server -y
RUN mkdir /var/run/sshd
RUN apt-get install openjdk-6-jdk
RUN echo "jenkins:jenkins" | chpasswd
RUN apt-get clean
RUN echo 'debconf debconf/frontend select Dialog' | debconf-set-selections
