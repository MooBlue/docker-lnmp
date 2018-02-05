FROM php:7.1-fpm

# 更改时区
ARG TIME_ZONE=UTC
ENV TIME_ZONE ${TIME_ZONE}
RUN ln -snf /usr/share/zoneinfo/$TIME_ZONE /etc/localtime && echo $TIME_ZONE > /etc/timezone

# 是否更换源
ARG CHANGE_SOURCE=false

RUN if [ ${CHANGE_SOURCE} = true ]; then \
	RUN mv /etc/apt/sources.list /etc/apt/source.list.bak
	COPY sources.list /etc/apt/sources.list
;fi

RUN  apt-get -o Acquire::Check-Valid-Until=false update && apt-get -y upgrade

# 安装基础组件
RUN apt-get install -y --no-install-recommends libpng-dev libjpeg-dev libfreetype6-dev ntpdate cron vim unzip git

# 安装扩展
RUN docker-php-ext-configure gd --with-freetype-dir --with-jpeg-dir
RUN docker-php-ext-install gd pdo_mysql mysqli

# 安装 Redis 扩展
COPY redis-3.1.3.tgz /home/redis.tgz
RUN pecl install /home/redis.tgz \
	&& echo "extension=redis.so" > /usr/local/etc/php/conf.d/redis.ini

# 安装 Mcrypt 加密扩展
COPY mcrypt-1.0.0.tgz /home/mcrypt.tgz
RUN apt-get install -y libmcrypt-dev libmhash-dev \
	&& pecl install /home/mcrypt.tgz \
	&& echo "extension=mcrypt.so" > /usr/local/etc/php/conf.d/mcrypt.ini

# 安装 composer
ADD composer.phar /usr/local/bin/composer
RUN chmod 755 /usr/local/bin/composer

# 是否设置中国源
RUN if [ ${CHANGE_SOURCE} = true ]; then \
	RUN composer config -g repo.packagist composer https://packagist.laravel-china.org
;fi