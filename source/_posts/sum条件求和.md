---
title: sum条件求和
date: 2015-06-23 17:55:42
categories: 数据库
tags: [数据库，索引]
---
## 基本用法
SUM函数的语法是： SELECT   SUM(expression )  FROM ables    WHERE    predicates;

表达式可以是一个数值字段或公式。

## 带条件的求和
类似条件表达式:SUM(IF(F_FILED1=1,A,B))
含义是如果F_FILED1等于1的话，那么就加上A，否则就加上B;

## 应用场景
### 计数
比如要统计一列中某些值出现的次数，可以使用group by；
但是，如果要求分组的条件不是具体值，而是集合，例如（2）、（1,3,4,5,6）
```sql
    SELECT COUNT(*) FROM T GROUP BY F1;
    # 这样子是按照值分组的
    
    SELECT SUM(IF(F1=2,1,0)) AS G1,SUM(IF(F1=2,0,1)) AS G2 FROM T GROUP BY F1;
    #这样子就可以解决问题
```    