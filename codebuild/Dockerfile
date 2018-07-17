FROM docker:dind

# update
RUN set -x && \
  apk update

# jq
RUN apk add --no-cache jq

# aws-cli
RUN apk --no-cache add python py-pip && \
  pip install --upgrade awscli

# java8
RUN apk --no-cache add openjdk8

# sbt
ENV SBT_HOME /usr/lib/sbt
ENV PATH $PATH:$SBT_HOME/bin

RUN apk add --no-cache bash \
  && apk add --no-cache --virtual=build-dependencies wget ca-certificates \
  && cd /usr/lib \
  && wget -q --no-cookies https://dl.bintray.com/sbt/native-packages/sbt/0.13.12/sbt-0.13.12.tgz -O - | gunzip | tar x \
  && apk del build-dependencies \
  && rm -rf /tmp/*

ENV LANG ja_JP.UTF-8
ENV LANGUAGE ja_JP:ja
ENV LC_ALL ja_JP.UTF-8
