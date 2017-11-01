# Structure

- config : 部署时， 各个模块使用的配置文件
- data : 部署后，需要导入的数据
- dist ： build输出目录
- extractor : 招标公告抽取服务
- pipeline ：数据存储处理服务
- publisher : 订阅服务
- registry : docker 仓库
- spider : 爬虫服务
- tools : 部署相关的脚本
- build.sh : 构建入口
- test.sh : 测试入口

# Build

### Prerequirement

docker images:
- python:2
- python:2.7-alpine
- redis:redis:3.0.7
- mongo:3.0.15


执行下列代码开始构建
```
git clone xxxx@gpu1080:/opt/BasinSpace/gitRepo/bidspy.git
cd bidspy
sh build.sh
```

执行后会自动将各个服务 build 成docker image。 然后将 image ， 配置文件和安装脚本 拷贝到 `bidspy/dist` 目录下。`bidspy/dist` 为发布目录.


---

# 测试环境部署

1. vagrant 虚拟机测试\(单机\)

    ```
    cd bidspy
    vagrant up
    ```


会自动启动一台 vagrant vm, 将 "./dist"  "/vagrant_data" 。

2. vagrant 多机测试

    ...

---

# 安装验证系统

1. 进入虚拟机

    ```
    sudo vagrant ssh (密码:vagrant)
    ```

2. 执行安装部署脚本

    部署docker镜像以及私有仓库

    ```
    cd /vagrant_data
    sh tools/install.sh
    ```

    需要指定vagrant ip, 目前已经内置了一个。

    注意：由于vagrant 的防火墙问题， 在脚本里加入了 `iptables -F` ，实体机安装需要考虑个更好的方法。

3. 启动服务

    ```
    docker-compose up
    ```

    需要指定docker 仓库 ip, 目前已经内置了一个

    mongodb map路径： /data/db_tmp/datadir
    redis map路径： /data/db_tmp/redis

    其他详情查看 docker-compose.yml

    注意：如果没有分配足够的存储，mongodb 可能无法启动


4. 导入数据

    ```
    cd tools && sh init_db.sh && cd -
    ```

4. 测试

    ```
    sh test.sh
    ```

    查看爬虫运行:
    http://10.142.55.199:50001

    查看结果（以部署在gpu1080为例）:
    http://10.142.55.199:50007/?task=test_result

-------------


**已知问题**:

1. vagrant ssh 进入需要密码\(可能权限问题\)

2. docker 需要rpm安装
https://docs.docker.com/engine/installation/linux/docker-ce/binaries/\#install-static-binaries  
https://download.docker.com/linux/static/stable/x86\_64/docker-17.09.0-ce.tgz

3. 目前的一键安装脚本是为了vagrant 测试所写，需要一个用于普通机器的安装脚本



