FROM ubuntu:18.04

MAINTAINER  ysslang <ysslang@qq.com>

ENV JAVA_VERSION=8 \
    JAVA_UPDATE=201 \
    JAVA_BUILD=09 \
    JAVA_HOME="/usr/lib/jvm/default-jvm" \
    LANG=C.UTF-8 \
    ORACLE_AUTHORIZATION_KEY=42970487e3af4f5aa5bca3f542482c60

RUN apt-get update && apt-get install -y --no-install-recommends \
    curl \
    unzip \
    && rm -rf /var/lib/apt/lists/* && \
    curl -jksSLH "Cookie: oraclelicense=accept-securebackup-cookie" -o /tmp/java.tar.gz \
        "http://download.oracle.com/otn-pub/java/jdk/${JAVA_VERSION}u${JAVA_UPDATE}-b${JAVA_BUILD}/${ORACLE_AUTHORIZATION_KEY}/jdk-${JAVA_VERSION}u${JAVA_UPDATE}-linux-x64.tar.gz" && \
    curl -jksSLH "Cookie: oraclelicense=accept-securebackup-cookie" -o /tmp/jce_policy-${JAVA_VERSION}.zip \
        "http://download.oracle.com/otn-pub/java/jce/${JAVA_VERSION}/jce_policy-${JAVA_VERSION}.zip" && \
    gunzip /tmp/java.tar.gz && \
    tar -C /tmp -xf /tmp/java.tar && \
    mkdir -p "/usr/lib/jvm" && \
    mv "/tmp/jdk1.${JAVA_VERSION}.0_${JAVA_UPDATE}" "/usr/lib/jvm/java-${JAVA_VERSION}-oracle" && \
    ln -s "java-${JAVA_VERSION}-oracle" "$JAVA_HOME" && \
    ln -s "$JAVA_HOME" /docker-java-home && \
    { \
        echo '#!/bin/sh'; \
        echo 'set -e'; \
        echo; \
        echo 'dirname "$(dirname "$(readlink -f "$(which javac || which java)")")"'; \
    } > /usr/local/bin/docker-java-home \
    && chmod +x /usr/local/bin/docker-java-home && \
    unzip -jo -d "$JAVA_HOME/jre/lib/security" "/tmp/jce_policy-${JAVA_VERSION}.zip" && \
    ln -s "$JAVA_HOME/bin/"* "/usr/bin/" && \
    rm -rf /tmp/*

WORKDIR /data

