---
title: "MySQL 的四种存储引擎"
date: 2019-03-04T10:00:00+08:00

author: "木杉"
categories: 
- MySQL
tags: 
- database
description: ""

draft: false
---

## MySQL 的四种存储引擎

#### InnoDB 存储引擎
* 支持事务处理，提供事务提交、回滚和崩溃恢复能力的事务安全。
* 支持行锁定，提高了多用户处理时的性能
* 为处理大数据设计，CPU处理效率比其他基于磁盘存储数据库的效率高
* 支持外键完整性约束
* 可以和其他存储引擎的数据混合查询
* 存储最大支持 64 TB

#### MyISAM 存储引擎
* 基于 ISAM 存储引擎并进行扩展，
* 拥有较高的的插入、查询速度，但不支持事务
* 存储最大支持 256 TB
* 数据文件和索引文件可放在不同目录下
* 每个字符列可以有不同的字符集

#### MEMORY 存储引擎
* 将数据存储在内存中

#### Archive 存储引擎
* 支持高并发插入，但本身不是事务安全
* 适合存储归档，如记录日志

功能 | MyISAM | MEMORY | InnoDB | Archive
--- | --- | --- | --- | ---
存储限制 | 256TB | RAM | 64TB | None
支持事务 | No | No | Yes | No
支持全文索引 | Yes | No | No | No
支持哈希索引 | No | Yes | No | No
支持数据缓存 | No | N/A | Yes | No
支持外键 | No | No | Yes | No
