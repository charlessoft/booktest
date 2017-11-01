# 研发环境

本章描述研发Basin平台的开发环境准备。

研发主机：10.142.55.199，各研发人员主机登录名名字首字母+姓全拼，缺省密码：abcd1234。登录后用passwd更改登录密码。  
$HOME目录下建立软链至/data/BasinSpace，该卷下有3.3T空间。研发用户属于basin组，该目录下对basin组开放所有访问权限，umask=002

开发语言：C++/Python/Shell/Go/JavaScript，禁用Java。

## 源代码管理

gitlab？ github?

## 测试集群

测试环境基于Vagrant，搭建4-6台主机组成的集群测试环境。操作系统选择CentOS? Ubuntu?

## 团队协作沟通

GitBook 所有开发文档入口，https://www.gitbook.com/@basinspace

Slack: basinspace.slack.com

Trello:

