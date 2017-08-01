FROM php:7.1-fpm

RUN touch /usr/local/etc/php/php.ini

# 安装 扩展
COPY redis-3.1.3.tgz /home/redis.tgz
RUN docker-php-ext-install pdo_mysql \
    && pecl install /home/redis.tgz && echo "extension=redis.so" > /usr/local/etc/php/conf.d/redis.ini

# 安装 composer
ADD composer.phar /usr/local/bin/composer
RUN chmod 755 /usr/local/bin/composer