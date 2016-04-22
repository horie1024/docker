FROM ubuntu:16.04

ENV DEBIAN_FRONTEND noninteractive

MAINTAINER Ryosuke Horie

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
  && cd /usr/local \
  && wget http://dl.google.com/android/android-sdk_r24.4.1-linux.tgz \
  && tar zxvf android-sdk_r24.4.1-linux.tgz \
  && rm -rf /usr/local/android-sdk_r24.4.1-linux.tgz

# Environment variables
ENV JAVA_HOME /usr/lib/jvm/java-8-oracle
ENV ANDROID_HOME /usr/local/android-sdk-linux
ENV PATH $ANDROID_HOME/platform-tools:$ANDROID_HOME/tools:$PATH

# Update of Android SDK
RUN echo y | android update sdk --no-ui --all --filter "android-23,build-tools-23.0.3" \
  && echo y | android update sdk --no-ui --all --filter "extra-google-m2repository,extra-android-m2repository"
