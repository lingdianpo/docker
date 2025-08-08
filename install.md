# docker安装

#### 下载并执行Docker官方安装脚本
    curl -fsSL https://get.docker.com -o get-docker.sh
    sudo sh get-docker.sh

#### 设置国内镜像
    sudo mkdir -p /etc/docker
    sudo tee /etc/docker/daemon.json <<-'EOF'
    {
    "registry-mirrors": ["https://******.mirror.aliyuncs.com"]
    }
    EOF
    sudo systemctl daemon-reload
    sudo systemctl restart docker



#### 设置代理（虚拟机上代理设置之后不起作用，先设置代理解决）

    vim /etc/systemd/system/docker.service.d/http-proxy.conf

    [Service]
    Environment="HTTP_PROXY=http://192.168.1.10:7890"
    Environment="HTTPS_PROXY=http://192.168.1.10:7890"
    Environment="NO_PROXY=localhost,127.0.0.1,::1"


#### 启动Docker服务
    sudo systemctl start docker
    sudo systemctl enable docker


# 安装docker-composer
    sudo curl -L "https://github.com/docker/compose/releases/download/v2.2.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
    
    sudo chmod +x /usr/local/bin/docker-compose
    
    sudo ln -s /usr/local/bin/docker-compose /usr/bin/docker-compose
    
    docker-compose version