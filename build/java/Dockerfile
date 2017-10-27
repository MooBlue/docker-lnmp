#使用的基础镜像
FROM registry.cn-hangzhou.aliyuncs.com/repos_zyl/centos:0.0.1

#下载安装包
RUN yum install -y wget
RUN wget http://archive.apache.org/dist/tomcat/tomcat-7/v7.0.75/bin/apache-tomcat-7.0.75.tar.gz
RUN wget http://7dx.pc6.com/wwb5/jdk7u79linuxx64.tar.gz

#解压安装包
RUN tar -zxvf apache-tomcat-7.0.75.tar.gz
RUN tar -zxvf jdk7u79linuxx64.tar.gz

#添加环境变量
ENV JAVA_HOME /jdk1.7.0_79
ENV CATALINA_HOME /apache-tomcat-7.0.75
ENV PATH $PATH:$JAVA_HOME/bin:$CATALINA_HOME/bin

#暴露8080端口
EXPOSE 8080

#启动时运行tomcat
CMD ["/apache-tomcat-7.0.75/bin/catalina.sh","run"]