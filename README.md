## 使用指南

Docker-LNMP 可以构建出基于 Docker 的 PHP 开发环境，其优势有在短时间内随意构建不同版本的相关服务、环境统一分布在不同服务器等，使开发者能够更专注于开发业务本身。

    当前版本   ：1.0
    默认服务   ：PHP-FPM 7.1、Nginx 1.12.1、mysql 5.6、redis 3.0、MongoDB Latest

#### 目录结构

    /docker-lnmp
        /build                  镜像构建目录
        /work                   持久化目录，包括 php 脚本、相关服务配置文件、数据库数据等
        /docker-compose.yml     compose 配置文件

#### 构建 Docker-LNMP

没有安装 Docker 的同学移步 [安装教程](https://github.com/beautysoft/docker-lnmp#安装-docker-及相关工具)

    cd ~/
    git clone https://github.com/beautysoft/docker-lnmp.git

    # 如果不在 ~/，自行修改 docker-compose.yml 的相关配置
    cd docker-lnmp
    sudo docker-compose up --build -d

#### 常用操作命令

    # 查看当前启动的容器
    sudo docker ps
    
    # 启动部分服务在后边加服务名，不加表示启动所有，-d 表示在后台运行
    sudo docker-compose up [nginx|php|mysql|redis|mongo] -d
    
    # 停止和启动类似
    sudo docker-compose stop [nginx|php|mysql|redis|mongo]
    
    # 如果更改了 dockerfile，比如在 php 里增加了一些其他扩展，需要重新编译
    sudo docker-compose build [php|...]

## 安装 Docker 及相关工具

1、安装 docker 参考 daocloud 提供的文档
    
    https://download.daocloud.io/Docker_Mirror/Docker

2、安装 docker-compose

    curl -L https://get.daocloud.io/docker/compose/releases/download/1.12.0/docker-compose-`uname -s`-`uname -m` > /usr/local/bin/docker-compose
    sudo chmod +x /usr/local/bin/docker-compose

    # 注意：你如果用的是非 root 用户，执行 curl 会提示没权限写入 /usr/local/bin 目录，可以先写入当前目录，再使用 sudo mv 过去  

3、启动 Docker

    sudo service docker start
    sudo docker info    

4、配置加速器（这简直是一定的）

    # 阿里云加速器
    # 每个人有对应的加速地址，访问 `https://dev.aliyun.com` ->【管理中心】-> 【DockerHub 镜像站点】配置加速器

    # DaoCloud 加速器配置文档
    # http://guide.daocloud.io/dcs/daocloud-9153151.html
