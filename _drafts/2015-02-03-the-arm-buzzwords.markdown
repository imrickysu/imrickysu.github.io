---
layout: post
title:  "那些ARM术语"
date:   2015-02-03 10:13:50
categories: ARM
---

读ARM相关文档的时候，总有那几个术语，无法在前后文中被自我解释，要弄懂他们必须要翻文档，但解释又非常含糊，又难记忆，每次看懂了过一阵子又忘记了，再查一回。

## Memory Ordering ##
- Normal
- Device
- Strongly Ordered

## Memory Attributes ##
### Shareability ###
- Non-shareable
- Inner shareable
- Outer shareable
- Full system

### Cacheability ###
- Write-back cacheable
- Write-through cacheable
- Non-cacheable

## Memory Barriers ##
- Data Memory Barrier (DMB)
- Data Synchronization Barrier (DSB)
- Instruction Synchronization Barrier (ISB)
