---
title: MySQL
description: 最广泛使用的单机数据库
date: 2024-09-10
weight: 1
---

## 架构

![mysql-architecture](/images/mysql/mysql-architecture.png)

可以看到MySQL是标准的C/S架构，客户端由各语言SDk或MySQL Shell命令行进行请求，由服务端进行响应，
本节主要介绍服务端模块架构：

- 