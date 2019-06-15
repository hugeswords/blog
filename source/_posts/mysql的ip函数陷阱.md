---
title: mysql的ip函数陷阱
date: 2018-11-09 12:01:25
categories: 数据库
tags: [数据库,网络]
photos: "2018/11/09/mysql的ip函数陷阱/inet.jpg"
---
## 简介
网络编程中经常涉及到ip地址的转化，inet_ntoa、 inet_aton、inet_addr是最基本的api;

原型：in_addr_t inet_addr(const char *cp);
参数：字符串，一个点分十进制的IP地址
返回值：32位网络字节序的ip

原型：int inet_aton(const char *string, struct in_addr*addr);
参数描述：
1 输入参数string包含ASCII表示的IP地址。
2 输出参数addr是32位网络字节序的ip

原型：char*inet_ntoa(struct in_addr in);
功能：将一个十进制网络字节序转换为点分十进制IP格式的字符串。

### 例子

``` cpp
    #include <iostream>
    #include <sys/socket.h>
    #include <netinet/in.h>
    #include <arpa/inet.h>
    using namespace std;
    int main(){
    
        struct in_addr my_addr1;
        struct in_addr my_addr2;
        char my_ip[] = "1.2.3.4";
        
        inet_aton(my_ip, &my_addr1);
        my_addr2.s_addr = inet_addr(my_ip);
    
        cout <<"inet_aton is [%d] "<<my_addr1.s_addr<<endl;
        cout <<"inet_addr is [%d] "<<my_addr2.s_addr<<endl;
    
        cout <<"inet_ntoa is [%s] "<< inet_ntoa(my_addr1)<<endl;
        cout <<"inet_ntoa is [%s] "<< inet_ntoa(my_addr2)<<endl;                                             
    
        return 0;
    
    }
	
    输出：
    inet_aton is [%d] 67305985
    inet_addr is [%d] 67305985
    inet_ntoa is [%s] 1.2.3.4
    inet_ntoa is [%s] 1.2.3.4
```

### 陷阱
对于网络编程很熟悉的人，知道这些api其实默认都是基于网络字节序的，网络字节序是大尾端，主机存储一般是小尾端。
mysql也提供的inet_aton和inet_ntoa这两个函数，但是他们默认是主机序的，和传统网络api刚好相反。
<img src="inet.jpg" width="80%" height="80%">