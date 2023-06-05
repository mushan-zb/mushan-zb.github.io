---
title: "protobuf 阅读指南"
date: 2020-07-01T10:00:00+08:00

author: "木杉"
categories: 
- protobuf
tags: 
- proto3
- protocol buffer
description: "本指南详细介绍如何使用 protocol buffer 语言构建 protocol buffer 数据。包括 .proto 的语法和如何使用 .proto 生成可访问的类"

draft: true
---

# [语言指南 - proto3]
本文是官方文档的不完全翻译（带有译者的主观意识）主要是为了以后有个方便的读文，另外锻炼自己的英语能力。借助了谷歌翻译、百度翻译

本指南详细介绍如何使用 protocol buffer 语言构建 protocol buffer 数据。包括 .proto 的语法和如何使用 .proto 生成可访问的类

## 定义消息类型
看一个简单的示例，假设定义一个搜索请求的消息格式。有三个参数：查询字符串，返回第几页数据，每页返回多少条记录。文件后缀为 .proto
``` demo-1.1
syntax = "proto3" // 规定使用的语法

message SearchRequest {
    string query = 1;
    int32 page_number = 2;
    int32 result_per_number = 3;
}
```
定义字段的格式：类型 变量名 = 编号;  
每一个字段都有一个唯一编号，字段编号将会用于消息二进制格式时标识这个字段，所以编号一旦使用就不应该更改
> **注：** 字段编号和类型共占字节数：编号 1 - 15 占一个字节，16 - 2047 占两个字节。频繁使用的字段尽量使用 1 - 15 的编号  
字段编号可使用范围：1 - 536,870,911(2^29-1)。不能使用编号 19000 - 19999（FieldDescriptor::kFirstReservedNumber through FieldDescriptor::kLastReservedNumber）该部分编号是为 protocol buffers 的实现保留的编号。也不能使用自己设置的保留字段编号

字段规则：
- 单数（singular）：字段有零个或一个值，这是 proto3 的默认规则
- 复数（repeated）：字段有零个或多个值（保留重复值和顺序），使用是需要在前面添加 repeated 关键字

### 定义多个字段
在一个 .proto 文件中可以定义多个 message，message 中也可以定义内部 message ；在其他 message 使用时用外部 message.内部 message 查找对应的 message 类型

注释使用 C/C++ 风格 // 或 /* ... */

### 保留字段






[语言指南 - proto3]:https://developers.google.com/protocol-buffers/docs/proto3