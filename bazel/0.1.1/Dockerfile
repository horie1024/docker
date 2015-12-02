FROM ubuntu:14.04

ENV DEBIAN_FRONTEND noninteractive

# install Java8
RUN sudo apt-get -y install software-properties-common \
  && sudo add-apt-repository -y ppa:webupd8team/java \
  && echo debconf shared/accepted-oracle-license-v1-1 select true | debconf-set-selections \
  && sudo apt-get -y update \
  && sudo apt-get -y install oracle-java8-installer

# download bazel installer
RUN sudo apt-get -y install wget \
  && wget https://github.com/bazelbuild/bazel/releases/download/0.1.1/bazel-0.1.1-installer-linux-x86_64.sh

# install bazel
RUN sudo apt-get -y install unzip \
  && sudo chmod +x bazel-0.1.1-installer-linux-x86_64.sh \
  && sudo ./bazel-0.1.1-installer-linux-x86_64.sh --user \
  && export PATH="$PATH:$HOME/bin"
