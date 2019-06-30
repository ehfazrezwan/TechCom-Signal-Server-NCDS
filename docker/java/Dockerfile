FROM frolvlad/alpine-java:latest
MAINTAINER Ehfaz Rezwan (ehfaz.rezwan@gmail.com)
# add the unlimited strength JCE policy for crypto
RUN apk upgrade --update && \
    apk add --update curl unzip && \
    curl -jksSLH "Cookie: oraclelicense=accept-securebackup-cookie" -o /tmp/unlimited_jce_policy.zip "http://download.oracle.com/otn-pub/java/jce/${JAVA_VERSION}/jce_policy-${JAVA_VERSION}.zip" && \
    unzip -jo -d ${JAVA_HOME}/jre/lib/security /tmp/unlimited_jce_policy.zip && \
    apk del curl unzip && \
    rm -rf /tmp/* /var/cache/apk/*
RUN apk add maven
COPY ../../service /usr/local/service