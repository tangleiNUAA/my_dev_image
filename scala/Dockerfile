FROM ubuntu:xenial

RUN apt-get update && \
    apt-get install -y less openjdk-8-jre-headless iproute2 vim-tiny sudo openssh-server && \
    rm -rf /var/lib/apt/lists/*

ENV SCALA_VERSION 2.11.12
ENV SCALA_HOME /opt/scala-$SCALA_VERSION
ENV PATH $SCALA_HOME/bin:$PATH

# Install Scala
ADD http://www.scala-lang.org/files/archive/scala-$SCALA_VERSION.tgz /
RUN (cd / && gunzip < scala-$SCALA_VERSION.tgz)|(cd /opt && tar -xvf -)
RUN rm /scala-$SCALA_VERSION.tgz
