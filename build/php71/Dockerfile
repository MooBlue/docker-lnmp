FROM php:7.1-fpm

# 复制扩展包
COPY redis-3.1.3.tgz /home/redis.tgz
COPY mcrypt-1.0.0.tgz /home/mcrypt.tgz

# 更换 apt-get 源
RUN mv /etc/apt/sources.list /etc/apt/source.list.bak
COPY sources.list /etc/apt/sources.list
RUN gpg --keyserver keyserver.ubuntu.com --recv-keys 40976EAF437D05B5
RUN gpg -a --export 40976EAF437D05B5 | apt-key add -

# 安装扩展依赖
RUN apt-get update && apt-get upgrade && apt-get install -y vi vim git libmcrypt-dev libmhash-dev

# 安装扩展
RUN docker-php-ext-install pdo_mysql \
    && pecl install /home/redis.tgz && echo "extension=redis.so" > /usr/local/etc/php/conf.d/redis.ini \
    && pecl install /home/mcrypt.tgz && echo "extension=mcrypt.so" > /usr/local/etc/php/conf.d/mcrypt.ini

# 安装 composer
ADD composer.phar /usr/local/bin/composer
RUN chmod 755 /usr/local/bin/composer

# 设置中国源
RUN composer config -g repo.packagist composer https://packagist.laravel-china.org