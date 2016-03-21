# DOCKER-VERSION 1.9.1
# VERSION        0.1
# SOURCE         https://github.com/mesosinfo/chronos

FROM ubuntu:14.04
MAINTAINER Yong Zhang<zhangyong.net@qq.com>

# Install dependancies
RUN apt-key adv --keyserver keyserver.ubuntu.com --recv E56151BF && \
echo deb http://repos.mesosphere.io/ubuntu trusty main > /etc/apt/sources.list.d/mesosphere.list && \
apt-get update

RUN apt-get install --assume-yes mesos python-software-properties curl default-jdk

## chronos ##
RUN apt-get -y install chronos

ENTRYPOINT ["mesos-chronos"]
