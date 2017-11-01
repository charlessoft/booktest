# 版本发布与部署

**BASINSPACE\_ROOT**_=/opt/BasinSpace            
_**BIDSPY\_ROOT**_=_**$BASINSPACE\_ROOT**_/bidspy_

源文件放在$BIDSPY_ROOT下。git仓库放在_**$BASINSPACE\_ROOT**_/gitRepo \(git clone xxx@gpu1080:/opt/BasinSpace/gitRepo/bidspy.git\)_

发布包放在$BASINSPACE\_ROOT/dist目录下

当前发布版本0.1，$BASINSPACE\_ROOT/dist/bidspy-0.1

测试环境4-6虚拟机，4G,  docker swarm

### docker服务标准

 - 将目前的配置文件全部改为环境变量设置
 - 使用link 连接各个服务

### 实际部署的测试与环境
 
 - 基础设施:

  - vagrant，不预装docker 等服务
  

 - 针对仓库机：

  - 安装docker
  - 安装docker swarm
  - 安装docker repository
  - 导入生产用的docker image
  
 
 - 针对其他机器：
  
  - 安装docker
  - 安装docker swarm
  - 从上述仓库机 docker repository 拉取所需的 image
  
 
 - 流程:
 
  - 从 安装依赖服务 -> 部署应用(docker)

### 开发的测试与环境

   - 基础设施:
   
    - vagrant/docker machine
    - 预先安装好docker, docker swarm 等必须服务
    - 开发的代码
    
   
   - 流程:
    - 部署应用(docker) -> 测试
   