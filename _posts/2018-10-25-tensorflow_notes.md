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

# tensorflow 学习笔记
## 基本知识
> tensorflow用graph表示计算任务（每一个结点为一个operation）
> graph需要在session中执行（session类比与一个与外部计算方式的入口）
> variable维护整个图的状态
> feed, fetch 为任意一个operation赋值或者获取数据
> 数据以tensor形式保存， tensor是一个numpy的ndarray对象


## 构建图
> 构建图第一步是构建多个操作（op）
> 将op添加进graph中
> 定义图
> 在session启动时， 如果没有显示的指定图， 则启动默认图。

### 图的管理
> 一个图包含一组operation对象
> graph始终有一个默认注册， 可以通过tf.get_default_graph()来访问
> 若使用默认graph， 则向graph中添加任何operation, 只需要定义operation， 则会自动添加进默认operation
> tf.Graph()新建一个图， 一般不新建。不同图之间的变量不会共享。


## 变量（variables)
#### 引自http://www.tensorfly.cn/tfdoc/api_docs/python/constant_op.html
### 常量初始化tensor函数
> tf.zeros(shape, dtype=tffloat32, name=None) 生成全零tensor
> tf.zeros_like(tensor, dtype=None, name=None) 生成和tensor一样的全零tensor
> tf.ones(shape, dtype=tf.float32, name=None) 生成全1tensor
> tf.ones_like(tensor, dtype=tf.float32, name=None) 生成和tensor形状一样的另一个tensor
> tf.fill(dims, value, name=None) 生成一个shape=dims的tensor，用value填充, dims, 和value均可是tensor
> tf.constant(value, dtype=None, shape=None, name='Const')

## python API

### 序列初始化函数
> tf.linspace(start, stop, num, name=None)  start到stop（闭区间）的等差序列共num个， start, stop需为tf.float
> tf.range(start, limit, delta=1, name='range') start到limit(半闭半开区间)的等差序列, 公差为delta

### 随机初始化tensor函数
> tf.random_normal(shape, mean=0.0, stddev=1.0, dtype=tf.float32, seed=None, name=None) 在正态分布均值为mean, 方差为stddev的情况下， 随机生成shape
> tf.truncated_normal(shape, mean=0.0, stddev=1.0, dtype=tf.float32, seed=None, name=None) 部分等价random_normal， 但是当生成的数值偏离大于2倍标准差会被丢弃重新生成
> tf.random_uniform(shape, minval=0.0, maxval=1.0, dtype=tf.float32, seed=None, name=None) 均匀分布（半开半闭区间）
> tf.random_shuffle(value, seed=None, name=None) value为一个tensor, 按照轴=0进行打乱



