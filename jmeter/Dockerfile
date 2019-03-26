FROM centos:7

MAINTAINER Herve Meftah <dockerlite@gmail.com>

ENV  JMETER_VERSION=5.1.1

RUN yum -y update && \
    yum -y install htop iotop, iftop git curl wget && \
    mkdir /jmeter   && \
    mkdir /scripts  && \
    mkdir /results

ENV JAVA_HOME /usr/lib/jvm/java-openjdk

RUN yum install -y java-1.8.0-openjdk-devel unzip curl vim python-setuptools sudo; \
    easy_install supervisor; \
    yum clean all

WORKDIR /tmp
RUN wget https://www-us.apache.org/dist//jmeter/binaries/apache-jmeter-${JMETER_VERSION}.tgz && \
    tar -zxvf apache-jmeter-${JMETER_VERSION}.tgz -C /jmeter

COPY maven-project.jmx /jmeter

WORKDIR /jmeter
VOLUME ["/results","/scripts"]
CMD ["/bin/bash"]
