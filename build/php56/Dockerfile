FROM php:5.6-fpm

# 安装 扩展
RUN apt-get update && apt-get -y --no-install-recommends install libssl-dev

COPY mongo.tgz /home/mongo.tgz

WORKDIR /home

RUN tar -zxvf mongo.tgz

WORKDIR /home/mongo-php-driver-legacy-master

RUN phpize && ./configure && make && make install && echo "extension=mongo.so" > /usr/local/etc/php/conf.d/mongo.ini
RUN docker-php-ext-install pdo_mysql