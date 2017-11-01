# 启动说明

#### 存储后端：

项目路径:/data/BasinSpace/src/universal\_backend  
启动：

```
docker run -d \
--name=ub \
-p 0.0.0.0:6000:6000 \
repository
```

#### 抽取服务:

项目路径:/data/BasinSpace/src/bidspy  
启动：

```
 docker run -d \
 --name=bidspy \
 -p 0.0.0.0:12000:5000 \
 extractor
```

#### etl服务：

项目路径:/data/BasinSpace/src/etl  
启动：

```
docker run -d \
--name=etl \
-p 7000:7000 \
--link ub:localhost \
pipeline
```

#### 查看结果：

[http://10.142.55.199:7000/?task=test\_result](http://10.142.55.199:7000/?task=test_result)  
不同的task需要自己指定。

#### 爬虫服务:

配置文件: config\_gpu/config.json

```
cd /data/BasinSpace/src/basin-spider
make run_gpu    # (docker-compose up -d)
(启动包含了pyspider, basin-spider, redis,mongo) 4个容器
```

#### 调度服务:

目前采集4个站点,**分4个配置文件来指定**

```
启动南网招标网站采集服务
docker run --rm \
    -v ${PWD}/config/publisher/config:/mnt/apps/workspace/publisher/config \
    publisher:1.0 \
    /bin/sh -c "cd publisher;python schedulercli.py -c ./config/config_csg.toml all"
```

```
启动安徽招标网站采集服务
docker run --rm \
    -v ${PWD}/config/publisher/config:/mnt/apps/workspace/publisher/config \
    publisher:1.0 \
    /bin/sh -c "cd publisher;python schedulercli.py -c ./config/config_ahbc.toml all"
```

```
启动政府招标网站采集服务
docker run --rm \
    -v ${PWD}/config/publisher/config:/mnt/apps/workspace/publisher/config \
    publisher:1.0 \
    /bin/sh -c "cd publisher;python schedulercli.py -c ./config/config_ccgp.toml all"
```

```
启动国网招标网站采集服务
docker run --rm \
    -v ${PWD}/config/publisher/config:/mnt/apps/workspace/publisher/config \
    publisher:1.0 \
    /bin/sh -c "cd publisher;python schedulercli.py -c ./config/config_sgcc.toml all"
```



