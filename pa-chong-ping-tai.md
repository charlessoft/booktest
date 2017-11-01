爬虫概述

爬虫基于pyspider开源架构,在此基础上进行改造,并在pyspider上层有一层basin-spider api层+爬虫脚本管理

1. pyspider
   1. 提供基础爬虫服务
2. basin-spider 
   1. 提供创建爬虫app和创建爬虫任务

代码目录:

/Data/BasinSpace/src/basin-spider

# Build

pyspider 镜像生成:

```
cd $BASINSPACE_ROOT/src/udb-spider
tar zcvf udb-spider.tar.gz pyspider udbswp tools
docker build -t pyspider:1.2 .

备注:可以直接执行make(默认 打包,编译镜像)
```

basin-spider 镜像生成:

```
cd $BASINSPACE_ROOT/src/basin-spider
tar zcvf basin-spider.tar.gz *
docker build -t basin-spider:1.2 .
备注:可以直接执行make(默认 打包,编译镜像)
```



