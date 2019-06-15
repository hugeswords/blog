---
title: perf简单使用
date: 2015-01-20 19:24:36
categories: 工具
tags: 工具
---
Perf 是用来进行软件性能分析的工具，非常强大的工具。
最初，perf叫做 Performance counter，在 2.6.31 内核中发布。在 2.6.32 中正式改名为 Performance Event，因为 perf 已不再仅仅作为 PMU 的抽象，而是能够处理所有的性能相关的事件。
perf能够分析程序运行期间发生的硬件事件，比如 instructions retired ，processor clock cycles ，多级cache的hit和miss，分支指令预测的错误率；也可以分析软件事件，比如 Page Fault 和进程切换。
而且，perf是随着内核一起发布的，就是说你装了linux就有了perf，使用起来也非常简单。
1.perf list                             #列出当前所支持的事件，不同平台有所差异
2.perf stat  ./a.out                #分析a.out，列出默认事件的信息
3.perf stat -e event  ./a.out  #选定事件分析a.out
4.perf top                             #类似于top
5.perf record -e event          #粒度更细，函数级别分析
6.perf report                         #和perf report一起使用