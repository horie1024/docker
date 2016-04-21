FROM ubuntu:16.04

ENV DEBIAN_FRONTEND noninteractive

RUN cd $HOME

# Install sudo
RUN apt-get update \
  && apt-get -y install sudo \
  && useradd -m docker && echo "docker:docker" | chpasswd && adduser docker sudo

# Install Java8
RUN sudo apt-get -y install software-properties-common \
  && sudo add-apt-repository -y ppa:webupd8team/java \
  && echo debconf shared/accepted-oracle-license-v1-1 select true | debconf-set-selections \
  && sudo apt-get -y update \
  && sudo apt-get -y install oracle-java8-installer

# Download Android SDK
RUN sudo apt-get -y install wget \
  && wget http://dl.google.com/android/android-sdk_r24.4.1-linux.tgz \
  && tar zxvf android-sdk_r24.4.1-linux.tgz

# Set ANDROID_HOME
RUN export ANDROID_HOME=$HOME/android-sdk-linux

# Set PATH
RUN export PATH=$ANDROID_HOME/platform-tools:$ANDROID_HOME/tools:$PATH

# Update Android SDK
RUN android update sdk --no-ui --all --filter "android-23,build-tools-23.0.3,extra-google-m2repository,extra-android-m2repository" 

