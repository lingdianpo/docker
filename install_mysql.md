# docker安装mysql

	docker pull mysql:5.7

#### 运行mysql

	docker run -p 3306:3306 --name mymysql -v $PWD/conf:/etc/mysql/conf.d -v $PWD/logs:/logs -v $PWD/data:/var/lib/mysql -e MYSQL_ROOT_PASSWORD=123456 -d mysql:5.7

	docker run -p 3307:3306 --name mymysql -v $PWD/docker_mysql/conf:/etc/mysql/conf.d -v $PWD/docker_mysql/logs:/logs -v $PWD/docker_mysql/data:/var/lib/mysql -e MYSQL_ROOT_PASSWORD=123456 -d mysql:5.7

#### 进入容器中

	docker exec -it mymysql /bin/bash

#### 登录mysql

	mysql -uroot -p123456

#### 设置mysql远程登录权限

	-- 1. 先创建/修改用户并设置密码
	CREATE USER IF NOT EXISTS 'lukejian'@'%' IDENTIFIED BY 'LXW1234lxw';
	CREATE USER IF NOT EXISTS 'lukejian'@'127.0.0.1' IDENTIFIED BY 'LXW1234lxw';
	CREATE USER IF NOT EXISTS 'lukejian'@'localhost' IDENTIFIED BY 'LXW1234lxw';

	-- 2. 然后授予权限
	GRANT ALL PRIVILEGES ON *.* TO 'lukejian'@'%' WITH GRANT OPTION;
	GRANT ALL PRIVILEGES ON *.* TO 'lukejian'@'127.0.0.1' WITH GRANT OPTION;
	GRANT ALL PRIVILEGES ON *.* TO 'lukejian'@'localhost' WITH GRANT OPTION;

	-- 3. 刷新权限
	FLUSH PRIVILEGES;