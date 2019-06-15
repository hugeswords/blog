---
title: STL系列三：forward_list
date: 2018-11-01 19:17:25
categories: STL
tags: [c++,STL]
---
## 简介
forward_list是一个顺序容器，它的插入和删除操作都是固定的时间。

它的实现是一个单向链表，所有的元素存储在不相关的内存区间，顺序试根据存储在元素中关联关系得到的。

forward_list和list的区别在于，前者元素中仅仅记录了指向下一个元素的连接，后者的每一个元素同时记录了2个连接（既有指向下一个元素的又有指向前一个元素的），当然这样是的list消耗了更多的存储空间。但是在插入和删除操作上，forward_list更加的高效。

和其他的顺序容器（array、vector、deque）相比较，forward_list在增删和移动数据上表现得更好，所以算法中大量的使用了它，比如排序算法。

链表和其他的顺序容器相比，缺少了直接根据位置访问元素的功能，不论访问哪一个元素，都必须从第一个元素开始遍历，当然这个访问时间是线性的，并且链表需要消耗更多的存储空间去记录元素之间的连接关系。

forward_list设计的初衷就是高效，和最简单的单项链表一样高效，事实上它是唯一个没有size这个成员函数的容器。因为每一次计算大小你都需要从头到尾遍历一遍，这很影响性能。或者使用一个计数器成员变量，每次增删元素都去更新一下计数，这个不仅消耗了额外的存储而且也十分影响性能。

## 使用方法
### 构造方法
``` cpp
    std::forward_list<int> first;                      // default: empty
    std::forward_list<int> second (3,77);              // fill: 3 seventy-sevens
    std::forward_list<int> third (second.begin(), second.end()); // range initialization
    std::forward_list<int> fourth (third);            // copy constructor
    std::forward_list<int> fifth (std::move(fourth));  // move ctor. (fourth wasted)
    std::forward_list<int> sixth = {3, 52, 25, 90};    // initializer_list constructor
```
### 访问方式
1.使用迭代器
2.新式for循环 for (int& x: mylist) 

### 常用函数
assign 赋值函数，使用一个链表的一部分去初始化另外一个链表

emplace_front 在链表头部插入元素

push_front 和emplace_front一回事，都是在头部插入新元素

pop_front 删除并返回链表头部

emplace_after 在迭代器后插入新元素，同时迭代器自增

insert_after 在迭代器后插入新元素，区别emplace_after的是可以插入多个元素

erase_after 删除迭代器后的一个或多个元素

swap  交换两个链表的内容

resize 调整大小，如果n小于当前size，就截断；如果n大于当前size，就使用尾部元素的值进行扩展。

clear 清空所有元素

splice_after 拼接两个链表

remove 删除指定值得元素

remove_if 牛逼，自定义一个bool类型的函数，判断链表中的元素是否满足这个函数的设定

unique 牛逼，也可以自定义比较i和i+1，注意使用这个得前提是显得进行排序

merge 合并两个链表

sort 排序，也可以自定义排序函数

reverse 链表反转
