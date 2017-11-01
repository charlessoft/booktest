# docker 基础镜像以及仓库构建

预先存储好docker 镜像的仓库

# 基于docker的开发流程

* 从构建好的仓库拉取基础镜像

* 使用基础镜像，将开发的程序打包成 服务镜像， 进行开发和测试

* 提交代码和 Dockerfile

* 将可release 的版本 导入到 docker repository里

# 简单服务串联流程

UI -&gt; 任务适配调度 -&gt; 爬虫 -&gt; 存储 -&gt; 任务适配调度 -&gt; 招标公告信息抽取服务 -&gt; 存储 -&gt; UI

# 基础必须部件

* docker 仓库，基础镜像

* 开发相关服务，并可打包进docker镜像

* 存储系统 \(可用容器暂替\)

* 资源管理，任务调度

# 其他功能部件

* 权限管理

* 性能

* 安全，容灾，备份

* UI

---

先从基础部件着手。

1. 仓库

   1. [https://docs.docker.com/registry/deploying/](https://docs.docker.com/registry/deploying/)

   2. [https://github.com/mkuchin/docker-registry-web](https://github.com/mkuchin/docker-registry-web)

2. 爬虫 镜像 与 api

3. 信息抽取 进项 与 api

4. 爬虫 -&gt; 信息抽取 的 中转处理程序



