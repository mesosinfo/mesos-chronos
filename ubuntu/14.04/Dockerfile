# DOCKER-VERSION 1.9.1
# VERSION        0.1
# SOURCE         https://github.com/mesosinfo/chronos

FROM ubuntu:14.04
MAINTAINER Yong Zhang<zhangyong.net@qq.com>

# Install dependancies
RUN apt-key adv --keyserver keyserver.ubuntu.com --recv E56151BF && \
echo deb http://repos.mesosphere.io/ubuntu trusty main > /etc/apt/sources.list.d/mesosphere.list && \
apt-get update
RUN sudo apt-get -y install curl python-setuptools python-pip python-dev python-protobuf

RUN sudo apt-get -y install mesos=0.28.0-2.0.16.ubuntu1404

## chronos ##
RUN apt-get -y install chronos=2.4.0-0.1.20150828104228.ubuntu1404

ENTRYPOINT ["mesos-chronos"]
