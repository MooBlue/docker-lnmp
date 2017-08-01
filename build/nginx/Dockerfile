FROM nginx:1.12.1

# 设置挂载目录
VOLUME ["nginx.conf:/etc/nginx/nginx.conf","conf.d:/etc/nginx/conf.d/","html:/etc/nginx/html/","logs:/var/log/nginx/"]

# 更改权限
RUN  chown -R www-data.www-data /etc/nginx/html/ /var/log/nginx/