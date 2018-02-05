FROM nginx:1.12.1

# 更改时区
ARG TIME_ZONE=UTC
ENV TIME_ZONE ${TIME_ZONE}
RUN ln -snf /usr/share/zoneinfo/$TIME_ZONE /etc/localtime && echo $TIME_ZONE > /etc/timezone

# 更改权限
RUN mkdir /etc/nginx/html
RUN chown -R www-data.www-data /etc/nginx/html/ /var/log/nginx/