---
title: 安装MongoDB
date: 2017-02-23 21:58:16
categories:
- 技术
- MongoDB
tags: MongoDB 

---

### 1.安装MongoDB

### 2.在安装目录下执行Mongod
cd: D:\Program Files\MongoDB\Server\3.2\bin
如果执行成功，会出输如下信息:
<!-- more -->

2015-09-25T15:54:09.212+0800 I CONTROL  Hotfix KB2731284 or later update is not
installed, will zero-out data files
2015-09-25T15:54:09.229+0800 I JOURNAL  [initandlisten] journal dir=c:\data\db\j
ournal
2015-09-25T15:54:09.237+0800 I JOURNAL  [initandlisten] recover : no journal fil
es present, no recovery needed
2015-09-25T15:54:09.290+0800 I JOURNAL  [durability] Durability thread started
2015-09-25T15:54:09.294+0800 I CONTROL  [initandlisten] MongoDB starting : pid=2
488 port=27017 dbpath=c:\data\db 64-bit host=WIN-1VONBJOCE88
2015-09-25T15:54:09.296+0800 I CONTROL  [initandlisten] targetMinOS: Windows 7/W
indows Server 2008 R2
2015-09-25T15:54:09.298+0800 I CONTROL  [initandlisten] db version v3.0.6


### 3.在安装目录下执行Mongo
cd: D:\Program Files\MongoDB\Server\3.2\bin
如果执行成功，输出如下：

MongoDB shell version: 3.0.6
connecting to: test

### 4.为了不用每次都进目录启服务，设置本地服务
mongod --logpath "D:/data/mongo.log" --logappend --dbpath "D:/data/db" --directoryperdb --serviceName "MongoDB" --serviceDisplayName "MongoDB" --install
 
### 5.启动服务
net start mongodb


### 异常：服务开启不了 发生服务特定错误: 100 发生服务特定错误: 48
#### 解决方案：
1，删除E:\MongoDB\data\mongod.lock文件
2，删除服务

mongod --logpath "D:/data/mongo.log" --logappend --dbpath "D:/data/db" --directoryperdb --serviceName "MongoDB" --serviceDisplayName "MongoDB" --remove

mongod --logpath "D:/data/mongo.log" --logappend --dbpath "D:/data/db" --directoryperdb --serviceName "MongoDB" --serviceDisplayName "MongoDB" --install