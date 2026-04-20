# docker安装nacos

	export NACOS_AUTH_TOKEN=$(openssl rand -base64 32)

	wN32jQ+H9MgtzuhZLnbbQ7ai6GAXN5OQdprEHN3TCOY=

	docker run --name nacos-standalone -e MODE=standalone -e JVM_XMS=512m -e JVM_XMX=512 -e JVM_XMN=256m -p 8848:8848 -d nacos/nacos-server:latest

	docker run --name nacos-standalone \
	  -e MODE=standalone \
	  -e JVM_XMS=256m \
	  -e JVM_XMX=512m \
	  -e JVM_XMN=256m \
	  -e NACOS_AUTH_TOKEN="$NACOS_AUTH_TOKEN" \
	  -e NACOS_AUTH_IDENTITY_KEY="serverIdentity" \
  	  -e NACOS_AUTH_IDENTITY_VALUE="nacosServer" \
	  -p 8848:8848 \
	  -p 8080:8080 \
	  -p 9848:9848 \
  	  -p 9849:9849 \
	  -v $PWD/nacos/nacos-data:/home/nacos/data \
	  -v $PWD/nacos/nacos-logs:/home/nacos/logs \
	  -d nacos/nacos-server:latest

# 图形界面地址
	http://192.168.1.11:8080


# 存储不够的时候查看是否有可扩展的存储

	vgs
	lvextend -L +5G /dev/mapper/ubuntu--vg-ubuntu--lv
	resize2fs /dev/mapper/ubuntu--vg-ubuntu--lv

	


