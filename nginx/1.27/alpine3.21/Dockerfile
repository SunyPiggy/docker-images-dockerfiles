FROM nginx:1.27.5-alpine3.21
ENV TZ=Asia/Shanghai
RUN sed -i 's/dl-cdn.alpinelinux.org/mirrors.aliyun.com/g' /etc/apk/repositories \
    && set -xe  \
    && cd /tmp/ \
    && apk add --no-cache --update --virtual .tzdata tzdata\
    && cp /usr/share/zoneinfo/${TZ} /etc/localtime \
    && echo ${TZ} > /etc/timezone \
    && rm -rf /tmp/*;