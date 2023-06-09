---
author: Nekilc
title: MySQL优化指南
date: 2019-10-10
tags: [mysql,backend,database]
---


## 连接器

- 不要频繁建立连接，使用长连接
- 大量长连接导致内存增长，定时关闭连接，在MySQL5.7及后续版本可以通过`mysql_reset_connection`重置连接。

## 查询缓存

- 尽量不要使用，如确需使用手动按需使用模式，
  - 配置：`query_cache_type = DEMAND` 
  - 使用：`mysql> select SQL_CACHE * from T where ID=10；`
- 在读远远多于写的情况可以使用

## 索引