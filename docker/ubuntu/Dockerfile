#FROM ubuntu
#RUN apt-get update && apt-get install vim
#FROM k8s.gcr.io/kube-apiserver:v1.12.0
/ 填写镜像维护者信息
FROM ubuntu:trusty
MAINTAINER Username<email@email.com>

// 安装运行环境
RUN apt-get update && \
    apt-get -y install \
    nginx \
    unzip \
    wget \
    ca-certification\
    php5 php5-fpm php5-cli php5-json php5-mysql php5-curl

// 安装pagekit

ENV PAGEJIT_VERSION 1.0.2
RUN mkdir /pagekit
WORKDIR /pagekit
VOLUME ["/pagekit/storage", "/pagekit/app/cache"]

// 从GitHub上拉取相应版本的Pagekit包

RUN Wget https://github.como/pagekit/release/download/$PAGEJIT_VERSION/pagekit-$PAGEJIT_VERSION/zip -O /pagekit/pagekit.zip && \ 
    unzip /pagekit/pagekit.zip && rm /pagekit/pagekit.zip

// 配置Nginx和清理镜像
ADD nginx.conf /etc/ngix/nginx.conf
RUN chown -R www-data: /pagekit && \
    apt-get autoremove wget unzip -y && \
    apy-get autoclean -y && \
    apt-get clean -y && \
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*
CMD ["sh", "-c", "service php5-fpm" start && nginx]
