---
title: STL系列一：array
date: 2018-11-01 10:24:13
categories: STL
tags: [c++,STL]
---
## 简介
array是固定元素数量的容器，不可以动态调整容器的大小，其实就是和数组一样。

## 使用方法

### 构造方式
array<Elem,N> c //默认构造函数; 创建一个默认初始化的数组
				//array<int, 100>并不会将元素初始化为0

array<Elem,N> c(c2) //复制构造函数; 创建另一个与c2同型的vector副本(所有元素都被复制)

array<Elem,N> c = c2 //复制构造函数; 创建另一个与c2同型的vector副本(所有元素都被复制)

array<Elem,N> c = initlist //使用初始化列表创建一个初始化的数组


### 访问方式

1.a[i],可以直接使用下标访问array的元素；

2.at(i),也可以

3.front(),返回第一个元素

4.back()，返回最后一个元素


### 常用函数
1.size()和max_size()都是指数组的大小，他们是一回事

2.bool empty()，数组大小为0就是空
