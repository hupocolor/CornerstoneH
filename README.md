# Cornerstone
新一代项目管理工具
全行业覆盖的一站式项目协作工具，集个人Portal、项目管理、团队协作、任务管理、测试管理、持续集成、Devops、CMDB、文件管理、Wiki管理于一体。
> 产品介绍：  https://www.cornerstone365.cn/cooperation.html#console

## 环境依赖
* 硬件：4G或以上内存，至少10G硬盘(推荐100G或以上）
* 操作系统：推荐Linux Centos7
* 数据库：Mysql5.7或以上

## 一键自动安装
- 宿主机部署
```
$ curl -sL http://install.cornerstone365.cn/github/script/install_cs_mysql.sh | sudo bash -
```
> 需要root账号执行<br>
> 默认安装路径/cshome
> 网页验证是否部署成功: http://[ip]:8888 默认账号：root 密码：ITITitit666
- docker部署
````
$ curl -sL http://install.cornerstone365.cn/github/script/docker_build_cs_mysql.sh | sudo bash -s 'youMysqlPassword'
````
> 如不指定数据库密码，默认使用uuid作为数据库密码

* [操作指导](#guidance)

## 上手指南

- [创建数据库](docs/db/数据库初始化手册.md)

- 本地数据库连接配置:<br>
  Cornerstone/CornerstoneBizSystem/local.properties
  ![localProperties.png](images/localProperties.png)
- Biz服务启动类:<br>
  Cornerstone/CornerstoneBizSystem/src/cornerstone/biz/CornerstoneBizSystem.java
  ![bizRun.png](images/bizRun.png)
- WEB服务启动类:<br>
  Cornerstone/CornerstoneWebSystem/src/cornerstone/web/CornerstoneWebSystem.java
  ![webRun.png](images/webRun.png)
- Web前端目录:<br>
  Cornerstone/CornerstoneWebSystem/websrc/<br>
  ![websrcPackage.png](images/websrcPackage.png)
- 本地启动:
> 查看下面本地启动
## 配置微信公众号
- [微信公众号配置](docs/wetchatoa/微信公众号配置.md)
## 项目目录结构描述
```
│ Cornerstone
├─docs 文档目录
│  ├─db    	数据库文档目录
│  └─mannual    用户操作手册
├─CornerstoneBizSystem 业务系统
│  └─src  业务系统源码目录
└─CornerstoneWebSystem Web系统
   └─websrc Web系统源码目录      
```

## 本地启动
> 启动前先查看上手指南
* 修改Biz服务local.properties数据库配置信息
* 启动Biz服务
* 启动web前端
* 进入 Cornerstone/CornerstoneWebSystem/websrc 
  > 如果没有安装node.js 请先安装node.js https://nodejs.org/
* 启动服务
````
$ npm i 
$ npm run serve
````
![npmRun.png](images/npmRun.png)
* 登录页面 （默认账号密码 root ITITitit666）<br>
![login.png](images/login.png)<br>
* [操作指导](#guidance)

## 编译
* 选择ant build.xml (CornerstoneBizSystem/build.xml、 CornerstoneWebSystem/build.xml)<br>
![chooseAnt.png](images/chooseAnt.png)
* ant构造Biz工程<br>
![buildBizAnt.png](images/buildBizAnt.png)
* 验证是否构造成功 验证文件：CornerstoneBizSystem/release/CornerstoneBizSystem.jaz
* 编译WEB(CornerstoneBebSystem/websrc)
````
$ npm i
$ npm run build
````
* ant构造web工程(等待biz ant构造完成)<br>
![buildWebAnt.png](images/buildWebAnt.png)
* 验证是否构造成功 验证文件：CornerstoneWebSystem/release/CornerstoneWebSystem.war
* 将CornerstoneBizSystem.jaz、CornerstoneWebSystem.war上传至linux系统
## Linux部署
* 获取cs目录结构
````
$ curl -O http://install.cornerstone365.cn/github/install/cshome.tar.gz
````
* 解压cs目录至服务器根目录
````
$ tar -zxvf cshome.tar.gz -C /
````
* 将CornerstoneBizSystem.jaz放在目录：/cshome/jazmin_server_jdk10/instance/CornerstoneBizSystem
* 将CornerstoneWebSystem.war放在目录：/cshome/jazmin_server_jdk10/instance/CornerstoneWebSystem
* 修改mysql连接配置: /cshome/jazmin_server_jdk10/instance/CornerstoneBizSystem/jazmin.js
* 启动cornerstone
* 网页验证是否部署成功: http://[ip]:8888
````
$ cd /cshome/jazmin_server_jdk10/
$ ./restartall.sh
````

## 功能示例
#### 首页
![process2.png](images/process2.png)
#### 报表
![report.png](images/report.png)
#### wiki
![wiki1.png](images/wiki1.png)
![wiki2.png](images/wiki2.png)
#### 任务
![task1.png](images/task1.png)
![task2.png](images/task2.png)
![task3.png](images/task3.png)
#### DevOps
![devops.png](images/devops.png)
### 流程审批
![process1.png](images/process1.png)
