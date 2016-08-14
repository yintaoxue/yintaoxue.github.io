---
layout: post
title: Kafka API和配置参数
date: 2016-07-29
category: design
author: ruogu
tags: [kafka]
---

## Producer

Producer是线程安全的，多线程共用一个实例比使用多个实例更快。

**send()**方法是异步的，消息会被存到缓存空间中，然后发送到集群。每个partition分别缓存，缓存区大小由batch.size设置，

**acks:all** 判断消息发送完成

**retries:0** 如果重试，消息有可能重复

**linger.ms** 延迟时间，等待消息组成batch一起发送，在负载比较高时，缓存区会很快被填满，会立即发送请求，低负载时改参数会损失一定的时效性。类似Nagle's algorithm in TCP.

**buffer.memory** 设置缓存的最大内存，缓存区被填满后，send的调用会被阻塞，如果超过max.block.ms时间，会抛出TimeoutException.

**key.serializer**和**value.serializer** key和value如何转换为bytes. StringSerializer, ByteArraySerializer.

**Producer参数：**http://kafka.apache.org/documentation.html#producerconfigs

#### 消息发送语义
[Message Delivery Semantics](http://kafka.apache.org/documentation.html#semantics)

* At most once - 消息可能丢失，但不会重复
* At least once - 消息不会丢失，但可能重复
* Exactly once - 消息只成功发送一次
Kafka默认保证at-least-once，可以通过设置retries=0来支持at-most-once

































