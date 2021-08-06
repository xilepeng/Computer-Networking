# Computer-Networking

### TCP 三次握手、四次挥手



```go
tcpdump -n -S -i en0  host www.baidu.com and tcp port 80
```

![截屏2021-08-06 10.30.48.png](http://ww1.sinaimg.cn/large/007daNw2ly1gt6vo07tx4j31z20ra7rj.jpg)

![截屏2021-08-06 10.39.42.png](http://ww1.sinaimg.cn/large/007daNw2ly1gt6voctk1zj31ew0feh37.jpg)


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


![截屏2021-08-06 10.44.40.png](http://ww1.sinaimg.cn/large/007daNw2ly1gt6vmys76nj30wk06adh0.jpg)


```go
x@n ~ curl www.baidu.com:80

<!DOCTYPE html>
<!--STATUS OK--><html> <head><meta http-equiv=content-type content=text/html;charset=utf-8><meta http-equiv=X-UA-Compatible content=IE=Edge><meta content=always name=referrer><link rel=stylesheet type=text/css href=http://s1.bdstatic.com/r/www/cache/bdorz/baidu.min.css><title>百度一下，你就知道</title></head> <body link=#0000cc> <div id=wrapper> <div id=head> <div class=head_wrapper> <div class=s_form> <div class=s_form_wrapper> <div id=lg> <img hidefocus=true src=//www.baidu.com/img/bd_logo1.png width=270 height=129> </div> <form id=form name=f action=//www.baidu.com/s class=fm> <input type=hidden name=bdorz_come value=1> <input type=hidden name=ie value=utf-8> <input type=hidden name=f value=8> <input type=hidden name=rsv_bp value=1> <input type=hidden name=rsv_idx value=1> <input type=hidden name=tn value=baidu><span class="bg s_ipt_wr"><input id=kw name=wd class=s_ipt value maxlength=255 autocomplete=off autofocus></span><span class="bg s_btn_wr"><input type=submit id=su value=百度一下 class="bg s_btn"></span> </form> </div> </div> <div id=u1> <a href=http://news.baidu.com name=tj_trnews class=mnav>新闻</a> <a href=http://www.hao123.com name=tj_trhao123 class=mnav>hao123</a> <a href=http://map.baidu.com name=tj_trmap class=mnav>地图</a> <a href=http://v.baidu.com name=tj_trvideo class=mnav>视频</a> <a href=http://tieba.baidu.com name=tj_trtieba class=mnav>贴吧</a> <noscript> <a href=http://www.baidu.com/bdorz/login.gif?login&amp;tpl=mn&amp;u=http%3A%2F%2Fwww.baidu.com%2f%3fbdorz_come%3d1 name=tj_login class=lb>登录</a> </noscript> <script>document.write('<a href="http://www.baidu.com/bdorz/login.gif?login&tpl=mn&u='+ encodeURIComponent(window.location.href+ (window.location.search === "" ? "?" : "&")+ "bdorz_come=1")+ '" name="tj_login" class="lb">登录</a>');</script> <a href=//www.baidu.com/more/ name=tj_briicon class=bri style="display: block;">更多产品</a> </div> </div> </div> <div id=ftCon> <div id=ftConw> <p id=lh> <a href=http://home.baidu.com>关于百度</a> <a href=http://ir.baidu.com>About Baidu</a> </p> <p id=cp>&copy;2017&nbsp;Baidu&nbsp;<a href=http://www.baidu.com/duty/>使用百度前必读</a>&nbsp; <a href=http://jianyi.baidu.com/ class=cp-feedback>意见反馈</a>&nbsp;京ICP证030173号&nbsp; <img src=//www.baidu.com/img/gs.gif> </p> </div> </div> </div> </body> </html>
```







