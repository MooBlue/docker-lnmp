FROM php:5.6-fpm

# 安装 扩展
COPY mongo-php /home/mongo
RUN apt-get update && apt-get -y --no-install-recommends install libssl-dev
WORKDIR /home/mongo/
RUN phpize && ./configure && make && make install && docker-php-ext-install pdo_mysql \
    && echo "extension=mongo.so" > /usr/local/etc/php/conf.d/mongo.ini