FROM redis:3.2

# 更改时区
ARG TIME_ZONE=UTC
ENV TIME_ZONE ${TIME_ZONE}
RUN ln -snf /usr/share/zoneinfo/$TIME_ZONE /etc/localtime && echo $TIME_ZONE > /etc/timezone

# 启动指定配置文件
CMD [ "redis-server", "/usr/local/etc/redis/redis.conf" ]