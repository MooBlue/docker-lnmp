# docker-lnmp
docker 结合 lnmp 的最佳实践

#### 安装 docker 及 docker-compose

    # 安装 docker，参考文档
    https://download.daocloud.io/Docker_Mirror/Docker
    
    # 安装 docker-compose
    curl -L https://get.daocloud.io/docker/compose/releases/download/1.12.0/docker-compose-`uname -s`-`uname -m` > /usr/local/bin/docker-compose
    sudo chmod +x /usr/local/bin/docker-compose
    
    # 注意你如果用的是非 root 用户，执行 curl 会提示没权限写入 /usr/local/bin 目录，可以先写入当前目录，再使用 sudo mv 过去
    
    # 启动 Docker
    sudo service docker start
    sudo docker info
    
    # 设置阿里云加速器（也可以使用其他加速器，比如 daocloud 的，文档自行查找）
    # 每个人有对应的加速地址，访问以下链接进入->【管理中心】-> 【DockerHub 镜像站点】配置加速器
    https://dev.aliyun.com/search.html
    
#### 构建 docker-lnmp

    # 下载 docker-lnmp
    cd ~/
    git clone https://github.com/beautysoft/docker-lnmp.git

    # 如果是其他路径（非 ~/），自行修改 docker-compose.yml
    cd docker-lnmp
    sudo docker-compose up --build -d
    
#### 常用命令

    # 查看当前启动的容器
    sudo docker ps
    
    # 启动部分服务在后边加服务名，不加表示启动所有，-d 表示在后在运行
    sudo docker-compose up [nginx|php|mysql|redis|mongo] -d
    
    # 停止跟启动类似
    sudo docker-compose stop [nginx|php|mysql|redis|mongo]
    
    # 如果更改了 dockerfile，比如在 php 里增加了一些其他扩展，需要重新编译
    sudo docker-compose build [php|...]
