---
title: "Elasticsearch 文档阅读"
date: 2020-06-01T20:00:00+08:00

author: "木杉"
categories: 
- 
tags: 
- 
description: ""

draft: true
---

# Elasticsearch 文档阅读【版本：7.1】
## 基本概念
### Near Realtime (NRT) - 近实时
ES 是一个近实时的搜索平台，从索引文档到要搜索的文档有一定的延时（通常为 1 秒）
### Cluster - 集群
集群是一个或多个节点的集合，共同保存数据并提供跨所有节点的联合索引和搜索服务。每一个集群必须有一个唯一的表示名，默认为“elasticsearch“
### Node - 节点
