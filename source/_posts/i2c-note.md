---
title: i2c-简记
date: 2023-06-01 09:03:24
tags: 
	- i2c
categories: tech
---

# i2c的特点

精简版，但遇到问题时从特征上分析可能看不出原因，多用来回顾

## 结构

- 两根线，SDA(data) + SCL (clock)
- 多主多从串行同步通信总线
- 上拉电阻 （空闲时为高电平）
- 线与机制
- 上升沿采样，下降沿变化
	1. SDA在SCL为低电平时才能改变
	2. SDA在SCL为高电平时保持，用于读取数据
	3. **START**标志-- SCL为高时，SDA由**高**变**低**
	4. **STOP**标志 -- SCL为高时，SDA由**低**变**高**

## 通信

+ Start & Stop
	1. 如果产生重复起始条件(Sr)而不产生停止条件，总线会一直处于busy。
	2. 一般Start& Stop 由 主机产生。

线与 和 多主
如何保证主机或从机发送数据时，其他从机或主机不会抢断？
ACK的过程是怎样的？ SDA被释放，此时SCL没有被释放， 那么SDA线的决定权为什么会来到从机？ 从机如何判断需要可以ACK
时间同步？  clock stretching

- **read**

- **write**

# i2c spec note

# **reference**

- :point_right: [i2c挂死分析和解决方法](https://www.jianshu.com/p/95f53ca2724e)
- :point_right: [i2c spec 翻译](https://zhuanlan.zhihu.com/p/149364473)
- :point_right: [原文链接](https://www.nxp.com.cn/docs/en/user-guide/UM10204.pdf)

{% cq %}**新闻已死**  {% endcq %}
