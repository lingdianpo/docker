#### 镜像列表

	docker images 

#### 删除镜像

	docker rmi 镜像id 

#### 拉取镜像

	docker pull 镜像名:版本号

#### 容器列表

	docker ps -a 

#### 查看日志

	docker logs 容器id

#### 删除容器

	docker rm 容器id

#### 进入到容器中

	docker exec -it 容器id /bin/bash  