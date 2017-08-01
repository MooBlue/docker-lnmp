FROM php:7.1-fpm

# 挂载配置文件
VOLUME ["php.ini:/usr/local/etc/php/php.ini","php-fpm.conf:/usr/local/etc/php-fpm.conf","php-fpm.d:/usr/local/etc/php-fpm.d/"]

COPY redis-3.1.3.tgz /home/redis.tgz
RUN docker-php-ext-install pdo_mysql \
    && pecl install /home/redis.tgz && echo "extension=redis.so" > /usr/local/etc/php/conf.d/redis.ini
ADD composer.phar /usr/local/bin/composer
RUN chmod 755 /usr/local/bin/composer