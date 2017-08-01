FROM nginx:1.12.1

# 设置挂载目录
VOLUME ["/etc/nginx/nginx.conf", "/etc/nginx/conf.d/", "/etc/nginx/html/", "/var/log/nginx/"]

# 更改权限
RUN  chown -R www-data.www-data /etc/nginx/html/ /var/log/nginx/