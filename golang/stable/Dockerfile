FROM golang:1.23.1-alpine3.20
WORKDIR /app
ENV TZ=Asia/Shanghai
RUN sed -i 's/dl-cdn.alpinelinux.org/mirrors.aliyun.com/g' /etc/apk/repositories \
    && set -xe  \
    && cd /tmp/ \
    && apk add --no-cache --update --virtual .tzdata tzdata\
    && cp /usr/share/zoneinfo/${TZ} /etc/localtime \
    && echo ${TZ} > /etc/timezone \
    && rm -rf /tmp/*;