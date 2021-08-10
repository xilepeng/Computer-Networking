# Computer-Networking


### OSI七层网络协议

![截屏2021-08-06 11.35.20.png](http://ww1.sinaimg.cn/large/007daNw2ly1gt6wyo315yj30xg0oktdo.jpg)


### TCP 三次握手、四次挥手



```go
tcpdump -n -S -i en0  host www.baidu.com and tcp port 80
```

![截屏2021-08-06 10.30.48.png](http://ww1.sinaimg.cn/large/007daNw2ly1gt6vo07tx4j31z20ra7rj.jpg)



```go
x@n ~ tcpdump -n -S -i en0  host www.baidu.com and tcp port 80

tcpdump: verbose output suppressed, use -v[v]... for full protocol decode
listening on en0, link-type EN10MB (Ethernet), snapshot length 262144 bytes
//三次握手
10:27:18.474807 IP 192.168.1.2.54365 > 39.156.66.18.80: Flags [S], seq 1551761630, win 65535, options [mss 1460,nop,wscale 6,nop,nop,TS val 716594132 ecr 0,sackOK,eol], length 0
10:27:18.514097 IP 39.156.66.18.80 > 192.168.1.2.54365: Flags [S.], seq 333727867, ack 1551761631, win 8192, options [mss 1444,nop,wscale 5,nop,nop,nop,nop,nop,nop,nop,nop,nop,nop,nop,nop,sackOK,eol], length 0
10:27:18.514169 IP 192.168.1.2.54365 > 39.156.66.18.80: Flags [.], ack 333727868, win 4096, length 0
//数据传输包
10:27:18.514245 IP 192.168.1.2.54365 > 39.156.66.18.80: Flags [P.], seq 1551761631:1551761708, ack 333727868, win 4096, length 77: HTTP: GET / HTTP/1.1
10:27:18.554787 IP 39.156.66.18.80 > 192.168.1.2.54365: Flags [.], ack 1551761708, win 916, length 0
10:27:18.556069 IP 39.156.66.18.80 > 192.168.1.2.54365: Flags [.], seq 333727868:333729308, ack 1551761708, win 916, length 1440: HTTP: HTTP/1.1 200 OK
10:27:18.556076 IP 39.156.66.18.80 > 192.168.1.2.54365: Flags [P.], seq 333729308:333730649, ack 1551761708, win 916, length 1341: HTTP
10:27:18.556202 IP 192.168.1.2.54365 > 39.156.66.18.80: Flags [.], ack 333730649, win 4052, length 0
10:27:18.556729 IP 192.168.1.2.54365 > 39.156.66.18.80: Flags [F.], seq 1551761708, ack 333730649, win 4096, length 0
10:27:18.566223 IP 39.156.66.18.80 > 192.168.1.2.54365: Flags [P.], seq 333729308:333730649, ack 1551761708, win 916, length 1341: HTTP
//四次挥手
10:27:18.566301 IP 192.168.1.2.54365 > 39.156.66.18.80: Flags [F.], seq 1551761708, ack 333730649, win 4096, options [nop,nop,sack 1 {333729308:333730649}], length 0
10:27:18.597221 IP 39.156.66.18.80 > 192.168.1.2.54365: Flags [.], ack 1551761709, win 916, length 0
10:27:18.597226 IP 39.156.66.18.80 > 192.168.1.2.54365: Flags [F.], seq 333730649, ack 1551761709, win 916, length 0
10:27:18.597351 IP 192.168.1.2.54365 > 39.156.66.18.80: Flags [.], ack 333730650, win 4096, length 0

10:27:18.605846 IP 39.156.66.18.80 > 192.168.1.2.54365: Flags [.], ack 1551761709, win 916, options [nop,nop,sack 1 {1551761708:1551761709}], length 0
10:27:21.643337 IP 39.156.66.18.80 > 192.168.1.2.54365: Flags [R], seq 333730650, win 0, length 0
```



```go
curl www.baidu.com:80
```

![截屏2021-08-05 19.04.07.png](http://ww1.sinaimg.cn/large/007daNw2gy1gt64ast8nlj61ky0m0e0a02.jpg)





```go
x@n ~ curl www.baidu.com:80

<!DOCTYPE html>
<!--STATUS OK--><html> <head><meta http-equiv=content-type content=text/html;charset=utf-8><meta http-equiv=X-UA-Compatible content=IE=Edge><meta content=always name=referrer><link rel=stylesheet type=text/css href=http://s1.bdstatic.com/r/www/cache/bdorz/baidu.min.css><title>百度一下，你就知道</title></head> <body link=#0000cc> <div id=wrapper> <div id=head> <div class=head_wrapper> <div class=s_form> <div class=s_form_wrapper> <div id=lg> <img hidefocus=true src=//www.baidu.com/img/bd_logo1.png width=270 height=129> </div> <form id=form name=f action=//www.baidu.com/s class=fm> <input type=hidden name=bdorz_come value=1> <input type=hidden name=ie value=utf-8> <input type=hidden name=f value=8> <input type=hidden name=rsv_bp value=1> <input type=hidden name=rsv_idx value=1> <input type=hidden name=tn value=baidu><span class="bg s_ipt_wr"><input id=kw name=wd class=s_ipt value maxlength=255 autocomplete=off autofocus></span><span class="bg s_btn_wr"><input type=submit id=su value=百度一下 class="bg s_btn"></span> </form> </div> </div> <div id=u1> <a href=http://news.baidu.com name=tj_trnews class=mnav>新闻</a> <a href=http://www.hao123.com name=tj_trhao123 class=mnav>hao123</a> <a href=http://map.baidu.com name=tj_trmap class=mnav>地图</a> <a href=http://v.baidu.com name=tj_trvideo class=mnav>视频</a> <a href=http://tieba.baidu.com name=tj_trtieba class=mnav>贴吧</a> <noscript> <a href=http://www.baidu.com/bdorz/login.gif?login&amp;tpl=mn&amp;u=http%3A%2F%2Fwww.baidu.com%2f%3fbdorz_come%3d1 name=tj_login class=lb>登录</a> </noscript> <script>document.write('<a href="http://www.baidu.com/bdorz/login.gif?login&tpl=mn&u='+ encodeURIComponent(window.location.href+ (window.location.search === "" ? "?" : "&")+ "bdorz_come=1")+ '" name="tj_login" class="lb">登录</a>');</script> <a href=//www.baidu.com/more/ name=tj_briicon class=bri style="display: block;">更多产品</a> </div> </div> </div> <div id=ftCon> <div id=ftConw> <p id=lh> <a href=http://home.baidu.com>关于百度</a> <a href=http://ir.baidu.com>About Baidu</a> </p> <p id=cp>&copy;2017&nbsp;Baidu&nbsp;<a href=http://www.baidu.com/duty/>使用百度前必读</a>&nbsp; <a href=http://jianyi.baidu.com/ class=cp-feedback>意见反馈</a>&nbsp;京ICP证030173号&nbsp; <img src=//www.baidu.com/img/gs.gif> </p> </div> </div> </div> </body> </html>
```




###  为什么 TIME_WAIT 等待的时间是 2MSL?

MSL 是 Maximum Segment Lifetime，报文最大生存时间，在 Linux 系统里 2MSL 默认是 60 秒，那么一个 MSL 也就是 30 秒。

1. 保证 TCP 协议的全双工连接能够可靠关闭
2. 保证这次连接的重复数据段从网络中消失

### 为啥会出现大量 close_wait ?

首先 close_wait 出现在被动关闭方

1. 并发请求太多导致
2. 被动关闭方未及时释放端口资源导致


### TCP 为啥需要流量控制？

1. 由于通讯双方网速不同，通讯方任意一方发送过快都会导致对方消息处理不过来，所以就需要把数据放到缓冲区中。
2. 如果缓冲区满了，发送方还在疯狂发送，那接收方只能把数据丢弃。因此我们需要控制发送速率。
3. 我们缓冲区剩余大小称之为接收窗口，用变量 win 表示。如果 win=0 ,则发送方停止发送。

### TCP 为啥需要拥塞控制？

1. 流量控制与拥塞控制是两个概念，拥塞控制是调节网络的负载。
2. 接收方网络资源繁忙，因未及时响应 ACK 导致发送方重传大量数据，这样将会导致网络更加拥堵。
拥塞控制是动态调整 win 大小，不只是依赖缓冲区大小确定窗口大小。

### TCP 拥塞控制

1. 慢开始与拥塞避免；
2. 快速重传与快速恢复。

### 为什么会出现粘包/拆包？

1. 应用程序写入的数据大于套接字缓冲区的大小，这将会发生拆包。
2. 应用程序写入的数据小于套接字缓冲区的大小，网卡将应用多次写入的数据写入到网络上，这将会发生粘包。
3. 进行 MSS(最大报文长度)大小的TCP分段，当TCP报文长度-TCP头部长度 > MSS 的时候将发生拆包。
（1 2 3 都发生在TCP层）
4. 接收方法不及时读取套接字缓冲区数据，这将发生粘包。




