# Django Cms Dockerfile
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
	sqlite3
RUN apt-get remove python-pip
RUN wget https://bootstrap.pypa.io/get-pip.py
RUN /usr/bin/python2.7 get-pip.py
RUN apt-get build-dep pillow -y
RUN pip install virtualenv --upgrade
RUN useradd djangocms
RUN mkdir /home/djangocms -p
RUN chown djangocms /home/djangocms
RUN locale-gen en_US.UTF-8
ENV LANG en_US.UTF-8  
ENV LANGUAGE en_US:en  
ENV LC_ALL en_US.UTF-8
USER djangocms
RUN cd /home/djangocms
RUN id
RUN virtualenv /home/djangocms/djangocms
RUN /home/djangocms/djangocms/bin/pip install djangocms-installer
RUN cd /home/djangocms/djangocms && /home/djangocms/djangocms/bin/djangocms -p . --starting-page yes -d sqlite://file///home/djangocms/djangocms/djangocms.db  -q  djangocms_demo
RUN echo "from django.contrib.auth.models import User; User.objects.create_superuser('admin', 'admin@example.com', 'djangocms')" | /home/djangocms/djangocms/bin/python /home/djangocms/djangocms/manage.py shell
USER root
RUN apt-get clean
RUN echo 'debconf debconf/frontend select Dialog' | debconf-set-selections
EXPOSE 8000
USER djangocms
WORKDIR /home/djangocms/djangocms
CMD bin/python manage.py runserver 0:8000
#CMD sudo -u djangocms /home/djangocms/djangocms/bin/python /home/djangocms/djangocms/manage.py runserver 0:8000
#CMD sudo -u djangocms /home/djangocms/djangocms/bin/python /home/djangocms/djangocms/manage.py runserver 0:8000
