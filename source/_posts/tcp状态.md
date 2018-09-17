---
title: tcp状态
date: 2018-09-17 19:39:05
categories: 网络
tags: 网络
---

<img src="tcp状态/tcp状态流转.gif" width="100%" height="100%">
全部11种状态
1. 客户端独有的：（1）SYN_SENT （2）FIN_WAIT1 （3）FIN_WAIT2 （4）CLOSING （5）TIME_WAIT 
2. 服务器独有的：（1）LISTEN （2）SYN_RCVD （3）CLOSE_WAIT （4）LAST_ACK 
3. 共有的：（1）CLOSED （2）ESTABLISHED 

各个状态的意义如下： 
(1)  LISTEN - 侦听来自远方TCP端口的连接请求； 
(2)  SYN-SENT -在发送连接请求后等待匹配的连接请求； 
(3)  SYN-RECEIVED - 在收到和发送一个连接请求后等待对连接请求的确认； 
(4)  ESTABLISHED- 代表一个打开的连接，数据可以传送给用户； 
(5)  FIN-WAIT-1 - 等待远程TCP的连接中断请求，或先前的连接中断请求的确认；
(6)  FIN-WAIT-2 - 从远程TCP等待连接中断请求； 
(7)  CLOSE-WAIT - 等待从本地用户发来的连接中断请求； 
(8)  CLOSING -等待远程TCP对连接中断的确认； 
(9)  LAST-ACK - 等待原来发向远程TCP的连接中断请求的确认； 
(10) TIME-WAIT -等待足够的时间以确保远程TCP接收到连接中断请求的确认； 
(11) CLOSED - 没有任何连接状态；
     
<img src="tcp状态/tcp_open_close.jpg" width="100%" height="100%">

<font size=6>1. TCP连接建立</font>
<font size=5>1.1 过程</font>
（1）客户 端发送一个带SYN标志的TCP报文到服务器。这是三次握手过程中的报文1。
（2）服务器端回应客户端的，这是三次握手中的第2个报文，这个报文同时带ACK标志和SYN标 志。因此它表示对刚才客户端SYN报文的回应；同时又标志SYN给客户端，询问客户端是否准备好进行数据通 讯。
（3）客户必须再次回应服务段一个ACK报文，这是报文段3。
<font size=5>1.2 为什么需要三次</font>
本质上是为了连接双方交换 ISN（Inital Sequence Number），另外 TCP 是全双工的协议，所以每次 SYN，都需要有对应的 ACK。加上服务端的 ACK 和 SYN 是在同一个包中，也就形成了 3 次握手。