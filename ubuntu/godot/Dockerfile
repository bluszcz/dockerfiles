# Godot CI Dockerfile
FROM ubuntu:14.04
MAINTAINER Rafał bluszcz Zawadzki <bluszcz@bluszcz.net>
RUN echo 'debconf debconf/frontend select Noninteractive' | debconf-set-selections
RUN apt-get update \ 
    && apt-get upgrade -y \ 
    && apt-get install -y -qq wget unzip libx11-6 \
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
RUN cd /opt \
    && wget https://downloads.tuxfamily.org/godotengine/2.1.1/Godot_v2.1.1-stable_export_templates.tpz \
    && mv Godot_v2.1.1-stable_export_templates.tpz Godot_v2.1.1-stable_export_templates.zip \
    && unzip Godot_v2.1.1-stable_export_templates.zip \
    && mkdir ~/.godot/ \
    && mv templates ~/.godot/ 

RUN ln -s /opt/Godot_v2.1-stable_x11.64 /bin/godot
RUN apt-get install -y xvfb x11vnc libegl1-mesa-drivers libegl1-mesa -y
RUN apt-get install -y kmod
RUN apt-get install -y linux-image-generic
RUN apt-get clean 
RUN mkdir ~/.vnc/
RUN x11vnc -storepasswd 1234 ~/.vnc/passwd-y

RUN apt-get install -y software-properties-common
RUN apt-add-repository ppa:webupd8team/java -y
RUN apt-get update
RUN echo "oracle-java8-installer shared/accepted-oracle-license-v1-1 select true" | sudo debconf-set-selections
RUN apt-get install oracle-java8-installer -y
RUN cd /opt/
RUN wget https://dl.google.com/android/android-sdk_r24.4.1-linux.tgz
RUN tar -zxvf android-sdk_r24.4.1-linux.tgz
RUN echo y |android-sdk-linux/tools/android update sdk -u -a -t 1,31 -s
RUN apt-get install -y scons

RUN mkdir /opt/godot-src/
RUN apt-get install -y gcc-mingw-w64-i686 mingw32 build-essential scons pkg-config libx11-dev libxcursor-dev libxinerama-dev \
    libgl1-mesa-dev libglu-dev libasound2-dev libpulse-dev libfreetype6-dev libssl-dev libudev-dev \
    libxrandr-dev
RUN cd /opt/godot-src \
    && wget https://github.com/godotengine/godot/archive/2.1.1-stable.tar.gz \
    && tar -zxvf 2.1.1-stable.tar.gz \
    && cd godot-2.1.1-stable \
    && pwd \
    && ls \ 
    && scons platform=server



RUN echo 'debconf debconf/frontend select Dialog' | debconf-set-selections

