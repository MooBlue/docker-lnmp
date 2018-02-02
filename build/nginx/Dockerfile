FROM nginx:1.12.1

# 更改时区
ENV TZ=Asia/Shanghai
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

# 更改权限
RUN mkdir /etc/nginx/html
RUN chown -R www-data.www-data /etc/nginx/html/ /var/log/nginx/