# 从零开始构建BasinSpace

> * [ ] 容器基础设施
> * [ ] 容器集群管理
> * [ ] 测试集群环境
> * [ ] 招标公告订阅系统

_**Despiser**_

## 容器基础设施

采用docke registry 自带仓库构建私有仓库镜像, 把需要的镜像push到registry中, 拷贝到无网络环境中安装仓库镜像,提供私有仓库服务.\(测试能闭环\)

操作系统: centos 7/redhat 6.8以上

必要软件:

* docker 使用yum install docker安装
* docker-compose 已自带,不需要单独安装
* docker registry 镜像

* **部署私有仓库**

* 安装私有仓库

> docker pull registry:2.6.2

* 运行docker registry镜像

  docker run -d -v `pwd`/registry-data:/var/lib/registry  -p 5000:5000 \

  ```
        --restart=always --name basinspace\_registry registry:2.6.22.
  ```

* 私有仓库地址:

> [http://127.0.0.1:5000](http://127.0.0.1:5000)

1. **私有仓库使用**

2. 获取私有仓库列表

> curl [http://127.0.0.1:5000/v2/\_catalog](http://127.0.0.1:5000/v2/_catalog)

返回

```
{"repositories":\["libs/docker.io/alpine"\]} 说明当前仓库已有的镜像
```

* 获取镜像列表

> curl [http://127.0.0.1:5000/v2/libs/docker.io/alpine/tags/list](http://127.0.0.1:5000/v2/libs/docker.io/alpine/tags/list)

返回

```
{"name":"libs/docker.io/alpine","tags":\["3.6"\]} 显示可以提供下载的tag列表
```

* 获取alpine镜像

> docker pull 127.0.0.1:5000/libs/docker.io/alpine:3.6

* 上传本地镜像到私有仓库

> docker tag docker.io/alpine:3.6 127.0.0.1:5000/libs/docker.io/alpine:3.6
>
> docker push 127.0.0.1:5000/libs/docker.io/alpine:3.6

```
备注: docker.io/alpine:3.6 为docker hub上下载的镜像
```

* 打包镜像\(导出\)

> docker save docker.io/registry &gt; registry2.6.2.tar

* 镜像导入

> docker load &lt; registry2.6.2.tar

## 容器集群管理

Nomad

Kubernetes

Rancher

Thrift

## 集群测试环境

## 招标公告订阅系统

## 现有模块集成

**存储后端**

项目地址：/data/BasinSpace/src/universal\_backend/  
地址：/data/BasinSpace/src/universal\_backend/  
目前集成db： MongoDB  
docker：

* name: universal\_backend
* port: 6000

**容器化 **

参数配置文件（bidspy.cfg\)格式：toml \(yaml, json, ini\)

toml: [https://github.com/toml-lang/toml](https://github.com/toml-lang/toml)  
c++: [https://github.com/skystrife/cpptoml](https://github.com/skystrife/cpptoml)  
python: [https://github.com/uiri/toml](https://github.com/uiri/toml)  
go: [https://github.com/BurntSushi/toml](https://github.com/BurntSushi/toml)  
java: [https://github.com/mwanji/toml4j](https://github.com/mwanji/toml4j)

爬虫、存储后端（Pyspider内置，mongo透明。）

DB：读写接口 1、 MongoDB 2、PostgreSQL

公告来源的范围。

抽取、（容器化）

输出: 公告的关键指标列表（招标单位、投标时间、金额）

简单的Web页面，输出指标，准确率？

系统状态可度量

**订阅主服务**

