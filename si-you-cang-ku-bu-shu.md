# 1.部署私有仓库

* 安装私有仓库

```
docker pull registry:2.6.2
```

* 运行docker registry镜像

  docker run -d -v `pwd`/registry-data:/var/lib/registry \  
        -p 5006:5000 \  
        --restart=always --name basinspace\_registry registry:2.6.2

运行后私有仓库地址为 [http://$](http://127.0.0.1:5000)PRIVATE\_REGISTRY[:500](http://127.0.0.1:5000)6

[**$**](http://127.0.0.1:5000)**PRIVATE\_REGISTRY** 为设定部署的ip地址

# 2. 私有仓库使用

修改docker配置

```
echo '{"insecure-registries":["'${PRIVATE_REGISTRY}'"]}' > /etc/docker/daemon.json
```

* 私有仓库列表

```
curl http://$PRIVATE_REGISTRY:5000/v2/_catalog
```

返回

```
{"repositories":\["libs/docker.io/alpine"\]} 说明当前仓库已有的镜像
```

* 获取镜像列表

```
curl http://$PRIVATE_REGISTRY:5006/v2/libs/docker.io/alpine/tags/list
```

返回

```
{"name":"libs/docker.io/alpine","tags":\["3.6"\]} 显示可以提供下载的tag列表
```

* 获取alpine镜像

```
docker pull $PRIVATE_REGISTRY:5006/libs/docker.io/alpine:3.6
```

* 上传本地镜像到私有仓库

```
docker tag docker.io/alpine:3.6 127.0.0.1:5000/libs/docker.io/alpine:3.6
docker push $PRIVATE_REGISTRY:5006/libs/docker.io/alpine:3.6
```

```
备注: docker.io/alpine:3.6 为docker hub上下载的镜像
```

* 打包镜像\(导出\)

```
docker save docker.io/registry > registry2.6.2.tar
```

* 镜像导入

```
docker load < registry2.6.2.tar
```





