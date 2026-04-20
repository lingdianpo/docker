# docker安装consul

	docker run -d -p 8500:8500 -p 8300:8300 -p 8301:8301 -p 8302:8302 -p 8600:8600/udp consul:1.15.4 agent -dev -client=0.0.0.0


	docker run -d -p 8500:8500 -p 8300:8300 -p 8301:8301 -p 8302:8302 -p 8600:8600/udp consul:1.15.4 agent -dev  -client=0.0.0.0

	docker container update --restart=always consul-server


#### 注意事项
浏览器访问 127.0.0.1:8500
 
dig @192.168.21.135 -p 8600 consul.service.consul SRV

docker设置代理的地方
 /etc/systemd/system/docker.service.d/http-proxy.conf


consul的api接口

进入docker容器
docker exec -it 容器id  sh

1.添加服务
https://www.consul.io/api-docs/agent/service#register-service
2.删除服务
https://www.consul.io/api-docs/agent/service#deregister-service
3.设置健康检查
https://www.consul.io/api-docs/agent/check
4.同一个服务注册多个实例

5.获取服务
https://www.consul.io/api-docs/agent/check#list-checks