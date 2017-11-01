# 招标公告订阅演示应用

从互联网公开的招标网站定期爬取招标公告，从网页文本中抽取招标公告的关键指标数据（包括招标项目、招标单位、投标时间、投标资质等），为订阅用户提供指定范围（行业、项目性质等）招标信息的主动推送订阅服务。

![](/assets/bidspy.png)

[dot文件](https://www.gitbook.com/book/basinspace/basin-space-knowledges/edit#/edit/master/bidspy.dot?_k=qqf2tx) \(dot -Tpng bidspy.dot -o bidspy.png\) [Graphviz Documentation](http://www.graphviz.org/Documentation.php), [Attributes](http://www.graphviz.org/content/attrs), [Node Shapes](http://www.graphviz.org/content/node-shapes#html), [Arrow Shapes](http://www.graphviz.org/content/arrow-shapes), [Colors](http://www.graphviz.org/content/color-names)

## 一、核心服务

## 1.1 订阅服务（publisher）

招标公告订阅系统的主服务，由订阅项目驱动，控制和支撑爬虫服务、抽取服务和推送服务。

### 1.1.1 订阅订单

由满足一个订阅用户的订阅需求的配置信息组成，由订阅服务唯一控制，实例来源可以是命令行参数、配置文件、全局配置中心等。  
&lt;样例&gt;

```toml
# 政府招标
# DB
[basinspace]
server = "10.142.55.199"
port= 5003

# etl
[etl]
server = "10.142.55.199"
port = "5008"
begintime="2017-10-26"
endtime="2017-10-29"

# 爬虫
[spider]
#server = "10.211.55.2"
server = "10.142.55.199"
port = 5001
task = "ccgp_zhaobiao_demo"
spiderapp = "ccgp_zhaobiao"


[[spider.data]]
 url = "http://www.ccgp.gov.cn/"
 [spider.data.extra]
     websiteName = "政府采购"
```

## 1.2 爬虫服务（spider）

受订阅服务控制，完成多个订阅项目指定网址的网页爬取任务，爬取的网页文本格式化后推送存储服务。

_**底层存储引擎是否采用sqlite?**_

## 1.3 抽取服务（extractor）

受订阅服务控制，完成多个订阅项目已爬取网页的抽取任务，并将抽结果保存在存储服务中。

## 1.4 投递服务（postman）

按订阅服务提供的订阅用户信息，从存储服务中获取抽取结果，格式化打包成订阅内容推送给订阅用户。

## 1.5 存储服务（repository）

提供容量无限的流式数据存储访问支持，该服务的核心实现会升级至BasinSpace平台，服务实际实现将弱化为统一存储访问接口，以适配器模式挂接各种后端。

## 二、应用可运行状态

**构建核心服务框架**

* [ ] 核心服务（订阅服务、爬虫服务、抽取服务、推送服务、存储服务）之间的连接关系。

**业务端到端功能需求描述**

* [ ] 输入端：订阅项目
* [ ] 输出端：指定时间段的订阅内容

**业务对象“订阅项目”驱动模型**

* [ ] 订阅项目
* [ ] 订阅内容

**各服务独立功能界定及功能实现架构分折**

* [ ] 订阅服务
* [ ] 爬虫服务
* [ ] 抽取服务
* [ ] 推送服务
* [ ] 存储服务

**核心服务可独立部署运行**

* [ ] 订阅服务

* [ ] 爬虫服务

* [ ] 抽取服务

* [ ] 推送服务

* [ ] 存储服务

**容器镜像支持（私有仓库、基础镜像造型等）**

* [ ] 私有仓库
* [ ] 基础镜像



