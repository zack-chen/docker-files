## 相关Docker命令：

创建镜像：
```
docker build -t dubbo-admin-tomcat:0.1 --rm=true .
```

列出镜像
```
docker images
```

如果要删除镜像，要先停止容器、删除容器，再删除镜像：
```
# 查看有哪些容器在运行
docker ps 

# 删除容器
docker rm $container_id

# 删除镜像
docker rmi $image_id

```

运行容器：
```
docker run -d -p 8000:8080 ${image_id}
# 说明：8000是宿主机端口，8080是映射到docker容器内的tomcat端口
```

进入容器
```
docker exec -it $container_id /bin/sh
```