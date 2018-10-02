---
layout:      post                     # 使用的布局
title:       Python Counter           # 标题
subtitle:    Python CookBook          # 副标题
date:        2018-09-30               # 时间
author:      ZJ                       # 作者
header-img:  img/post-bg-2015.jpg     # 这篇文章标题背景图片
catalog:     true                     # 是否归档
tags:                                 # 标签
    - 学习
---
# Python Counter 学习及设计剖析
## Counter 类简介
> Counter是python collections模块的一个类。主要用来统计可迭代数据的个数特性。
>
> 计算结果以字典形式保存。键为被统计的元素,值为元素的个数。

## Counter 常用函数
>
### Counter 初始化
> Counter 初始化传入为可迭代对象或空（Counte(iterable=None)）。

### update
> update方法，对一个可迭代数据进行个数统计，有两个地方会用到。
>> * Counter类初始化时。
>> * 传入一个可迭代数据，对Counter类的统计数据进行更新。

### most_common
> most_common 方法， 参数为 n 。
>
> 输出Counter类中统计前n的数据。以list方式输出， 每一个元素为一个tuple类型，第一位为统计元素，第二位为统计次数。
>> * 内部实现为堆（待后续具体分析）

### 其他特性
> * 支持两个Counter实例的加法。 返回两个实例元素之和。(效果上等效于Counter的update功能)
> * 支持两个Counter实例的减法。仅返回统计次数为正的结果。
> * 支持两个Counter的并集。如果两个Counter含有的键值相同，返回统计次数最大的一个。
> * 支持两个Counter的交集。返回统计次数最小的一个（有相同键值情况下）。

