FROM php:7.2.8-fpm-stretch

ENV PHP_DEPS \
		autoconf \
                libldap2-dev \
		libldap-2.4-2 \
		libtool-bin \
		libzip-dev \
		lbzip2 \
		libxml2-dev \
		bzip2 \
		re2c \
		libbz2-dev \
		apache2-dev \
		libjpeg-dev \
		libxpm-dev \
		libxpm-dev \
		libgmp-dev \
		libgmp3-dev \
		libmcrypt-dev \
		mysql-server \
		mysql-common \
		libpspell-dev \
		librecode-dev \
		libcurl4-openssl-dev \
		libxft-dev

RUN apt-get clean \
    && apt-get update --fix-missing \
    && apt-get install -y \
		$PHP_DEPS \
		ca-certificates \
		curl \
		xz-utils \
	--no-install-recommends && rm -r /var/lib/apt/lists/* \
    && docker-php-ext-configure pdo_mysql --with-pdo-mysql=mysqlnd \
    && docker-php-ext-install pdo_mysql \
    && docker-php-ext-configure mysqli --with-mysqli=mysqlnd \
    && docker-php-ext-install mysqli \
    && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/lib \
    && docker-php-ext-install redis \
    && docker-php-ext-install memcached \
    && docker-php-ext-install -j$(nproc) gd soap intl gmp bcmath mbstring zip pcntl sockets bz2 shmop readline exif opcache \
    && apt-get purge -y --auto-remove $PHP_DEPS
