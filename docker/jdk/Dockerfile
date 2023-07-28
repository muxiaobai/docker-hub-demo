
#FROM frolvlad/alpine-glibc:alpine-3.8
FROM frolvlad/alpine-java:jdk8.202.08-slim
MAINTAINER muxiaobai<zpf12345678910@email.com>
#ADD jdk-8u201-linux-x64.tar.gz /usr/local/
#ENV JAVA_HOME /usr/local/jdk1.8.0_201
#ENV PATH  ${PATH}:${JAVA_HOME}/bin
#ENV CLASSPATH ${JAVA_HOME}/lib/dt.jar:${JAVA_HOME}/lib/tools.jar
COPY --from=hengyunabc/arthas:latest /opt/arthas /opt/arthas
RUN echo 'Asia/Shanghai' >/etc/timezone
RUN apk add --no-cache net-tools curl gcc python httpd-tools
RUN sed -i 's~dl-cdn.alpinelinux.org~mirrors.aliyun.com~' /etc/apk/repositories \
        && apk --update --no-cache add bash \
        bash-doc \
        bash-completion \
        && rm -rf /var/cache/apk/*
