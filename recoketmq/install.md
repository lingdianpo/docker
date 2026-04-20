
## 使用说明


   # 在宿主机上创建并设置正确的权限
   mkdir -p ./data/broker/logs ./data/broker/store

   # 设置权限为所有用户可写（因为容器内 rocketmq 用户需要写入）
   chmod -R 777 ./data/broker/logs ./data/broker/store


1. 将上述内容保存为 `docker-compose.yml` 文件

2. 在文件所在目录执行以下命令启动服务：
   ```bash
   docker-compose up -d
   ```

3. 查看运行状态：
   ```bash
   docker-compose ps
   ```

4. 停止服务：
   ```bash
   docker-compose down
   ```

5. 如果需要查看日志：
   ```bash
   docker-compose logs -f    --tail 30
   ```

6. 查看集群列表：
   ```bash
   docker exec -it -u root rocketmq-broker bash -c "/home/rocketmq/rocketmq-4.9.7/bin/mqadmin clusterList -n rocketmq-namesrv:9876"
   ```