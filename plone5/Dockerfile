# Plone 5.0rc2 Dockerfile
FROM ubuntu:14.04
MAINTAINER Rafał bluszcz Zawadzki <bluszcz@bluszcz.net>
RUN echo 'debconf debconf/frontend select Noninteractive' | debconf-set-selections
RUN apt-get update
RUN apt-get upgrade -y
# pip seems be messed up in Ubuntu Trusty source:
# https://bugs.launchpad.net/ubuntu/+source/python-pip/+bug/1306991
# https://bugs.launchpad.net/ubuntu/trusty/+source/python-pip/+bug/1308714
RUN apt-get install python2.7-dev \ 
	wget -y \
	libxml2-dev \
	libxslt1-dev
RUN apt-get remove python-pip
RUN wget https://bootstrap.pypa.io/get-pip.py
RUN /usr/bin/python2.7 get-pip.py
RUN apt-get build-dep pillow -y
RUN pip install virtualenv --upgrade
RUN useradd plone
RUN mkdir /home/plone
RUN chown plone /home/plone 
USER plone
RUN cd /home/plone
RUN id
RUN virtualenv /home/plone/plone5
RUN cd /home/plone/plone5
RUN /home/plone/plone5/bin/pip install zc.buildout
RUN cd /home/plone/plone5 && bin/buildout init
RUN echo  "[buildout]\nextends =  https://raw.github.com/bluszcz/pins/master/plone-5-0" >/home/plone/plone5/buildout.cfg
RUN cd /home/plone/plone5 && bin/buildout 
USER root
RUN apt-get clean
RUN echo 'debconf debconf/frontend select Dialog' | debconf-set-selections
EXPOSE 8080
CMD sudo -u plone /home/plone/plone5/bin/plone fg
