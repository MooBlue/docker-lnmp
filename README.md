## Docker-LNMP 使用指南

### 目录结构

    /docker-lnmp
        /build                  镜像构建目录
        /work                   资源映射目录，可以在这里放置 php 脚本及服务相关的配置文件
        /docker-compose.yml     compose 配置文件

### 安装 docker 和 docker-compose

1、安装 docker，参考 daocloud 提供的文档
    
    https://download.daocloud.io/Docker_Mirror/Docker

2、安装 docker-compose

    curl -L https://get.daocloud.io/docker/compose/releases/download/1.12.0/docker-compose-`uname -s`-`uname -m` > /usr/local/bin/docker-compose
    sudo chmod +x /usr/local/bin/docker-compose    

注意：你如果用的是非 root 用户，执行 curl 会提示没权限写入 /usr/local/bin 目录，可以先写入当前目录，再使用 sudo mv 过去
    
3、启动 Docker

    sudo service docker start
    sudo docker info    

4、设置加速器（这简直是一定的），举例阿里云加速器，也可以使用其他加速器，比如 DaoCloud ，文档自行查找，每个人有对应的加速地址，访问 `https://dev.aliyun.com/search.html` ->【管理中心】-> 【DockerHub 镜像站点】配置加速器

### 构建 docker-lnmp

    cd ~/
    git clone https://github.com/beautysoft/docker-lnmp.git

    # 如果不在 ~/，自行修改 docker-compose.yml 的相关配置
    cd docker-lnmp
    sudo docker-compose up --build -d

### 常用命令

    # 查看当前启动的容器
    sudo docker ps
    
    # 启动部分服务在后边加服务名，不加表示启动所有，-d 表示在后在运行
    sudo docker-compose up [nginx|php|mysql|redis|mongo] -d
    
    # 停止和启动类似
    sudo docker-compose stop [nginx|php|mysql|redis|mongo]
    
    # 如果更改了 dockerfile，比如在 php 里增加了一些其他扩展，需要重新编译
    sudo docker-compose build [php|...]
