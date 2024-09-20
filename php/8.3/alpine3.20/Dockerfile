#
# NOTE: THIS DOCKERFILE IS GENERATED VIA "apply-templates.sh"
#
# PLEASE DO NOT EDIT IT DIRECTLY.
#

FROM php:8.3.11-fpm-alpine3.20

	#自定义配置
	# zlib-dev \
	# libzip-dev \
	# libpng-dev \
	# libjpeg-turbo-dev \
	# freetype-dev \
	# libmemcached-dev \

	# #自定义配置
	# --enable-bcmath \
	# --enable-sockets \
	# --enable-soap \
	# --enable-pcntl \
	# --with-mysqli \
	# --with-pdo-mysql \
	# --with-jpeg \
	# --with-freetype \
	# --enable-gd \
ENV TZ=Asia/Shanghai
RUN sed -i 's/dl-cdn.alpinelinux.org/mirrors.aliyun.com/g' /etc/apk/repositories \
	&& set -xe  \
	&& cd /tmp/ \
	&& apk add --no-cache --update --virtual .tzdata tzdata\
	&& cp /usr/share/zoneinfo/${TZ} /etc/localtime \
	&& echo ${TZ} > /etc/timezone; \
	apk add --no-cache libstdc++ libpq  libmemcached-dev && \
	apk add --no-cache --virtual .build-deps \
	$PHPIZE_DEPS \
	libzip-dev \
	libpng-dev \
	libjpeg-turbo-dev \
	freetype-dev \
	curl-dev \
	zlib-dev \
	sqlite-dev \
	libpq \
	pcre-dev \
	pcre2-dev \
	postgresql-dev \
	unixodbc-dev \
	linux-headers \
	brotli-dev  \
	nghttp2 \
	nghttp2-dev \
	libxml2-dev \
	; \
	docker-php-ext-configure gd --with-freetype --with-jpeg \
	&& docker-php-ext-install -j$(nproc) \
	bcmath \
	sockets \
	soap \
	pcntl \
	gd \
	opcache; \
	pecl channel-update pecl.php.net; \
	pecl install igbinary; \
    pecl install memcached; \
    pecl install redis; \
    pecl install --configureoptions 'enable-sockets="yes" enable-openssl="yes" enable-mysqlnd="yes" enable-swoole-curl="yes" enable-cares="yes" enable-brotli="yes" enable-swoole-pgsql="yes" with-swoole-odbc="unixODBC,/usr"  enable-swoole-sqlite="yes"' swoole; \
    pecl install xdebug; \
    docker-php-ext-enable igbinary memcached  redis swoole xdebug; \
    rm -rf /tmp/* \
    && apk del .build-deps \
	&& rm -rf /var/cache/apk/*
#自定义配置 安装 igbinary memcached，redis，swoole，xdebug