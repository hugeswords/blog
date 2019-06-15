---
title: STL系列二：deque
date: 2018-11-01 11:15:35
categories: STL
tags: [c++,STL]
---
## 简介
deque是double-ended queue的简写，代表双向队列。它是一个顺序容器，并且可以动态的调整大小，在头部和尾部都可以进行扩展。
看起来deque和vector有些类似，他们在头部和尾部进行插入、删除操作都有着很高的效率，不同的是，deque并不保证它的元素都存储在连续的内存空间，使用指针便宜去访问deque中的元素是非法操作。
vector使用的是一个简单的数组来进行存储，当然这个数组可能会被进行扩展，但是deque存储在不同的内存块上，所以当元素特别多的时候，deque在扩展的时候比vector更有效率。

## 使用方法
### 构造方法
  std::deque<int> first;                                // empty deque of ints
  
  std::deque<int> second (4,100);                       // four ints with value 100
  
  std::deque<int> third (second.begin(),second.end());  // iterating through second
  
  std::deque<int> fourth (third);                       // a copy of third

### 访问方式
1.a[i],可以直接使用下标访问array的元素；

2.at(i),也可以

3.front(),返回第一个元素

4.back()，返回最后一个元素

### 常用函数
1.bool empty() 判断队列是否为空

2.size() 返回队列的大小

2.删除某个元素（疑惑，队列应该不允许随意删除元素）
iterator erase (iterator position);
iterator erase (iterator first, iterator last);

3.插入元素（疑惑，这是插队啊）
insert (iterator position, const value_type& val);	
void insert (iterator position, size_type n, const value_type& val);

4.swap(deque& x)交换两个队列的内容（这个感觉可以用赋值运算代替）

5.精华函数,作为一个双向队列必须有这几个函数
pop_front() 返回并弹出头部元素

pop_back()  返回并弹出尾部元素

push_front() 插入一个头部元素

push_back()  插入一个尾部元素

6.void shrink_to_fit();
让队列减少内存空间，仅使用和它的大小匹配的内存就可以。因为大多数的队列是通过动态数组实现的；