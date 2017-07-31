FROM nginx:1.12.1

ADD  nginx.conf      /etc/nginx/nginx.conf
ADD  conf.d/*    	 /etc/nginx/conf.d/
RUN  mkdir /opt/htdocs && mkdir /opt/log && mkdir /opt/log/nginx
RUN  chown -R www-data.www-data /opt/htdocs /opt/log

VOLUME ["/opt"]