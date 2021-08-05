# Computer-Networking

### TCP 三次握手、四次挥手

```go
curl www.baidu.com:80
```
![截屏2021-08-05 19.04.07.png](http://ww1.sinaimg.cn/large/007daNw2gy1gt64ast8nlj61ky0m0e0a02.jpg)


```go
tcpdump -n -S -i en0  host www.baidu.com and tcp port 80
```

![截屏2021-08-05 18.58.53.png](http://ww1.sinaimg.cn/large/007daNw2gy1gt646jq94cj61yu0nq7pm02.jpg)


```go
tcpdump: verbose output suppressed, use -v[v]... for full protocol decode
listening on en0, link-type EN10MB (Ethernet), snapshot length 262144 bytes
//三次握手
18:57:41.545079 IP 192.168.1.2.59676 > 103.235.46.39.80: Flags [S], seq 2463422552, win 65535, options [mss 1460,nop,wscale 6,nop,nop,TS val 1575594831 ecr 0,sackOK,eol], length 0
18:57:41.627961 IP 103.235.46.39.80 > 192.168.1.2.59676: Flags [S.], seq 305454062, ack 2463422553, win 8192, options [mss 1452,nop,wscale 5,nop,nop,nop,nop,nop,nop,nop,nop,nop,nop,nop,nop,sackOK,eol], length 0
18:57:41.628110 IP 192.168.1.2.59676 > 103.235.46.39.80: Flags [.], ack 305454063, win 4096, length 0

18:57:41.628246 IP 192.168.1.2.59676 > 103.235.46.39.80: Flags [P.], seq 2463422553:2463422630, ack 305454063, win 4096, length 77: HTTP: GET / HTTP/1.1
18:57:41.711331 IP 103.235.46.39.80 > 192.168.1.2.59676: Flags [.], ack 2463422630, win 776, length 0
18:57:41.730591 IP 103.235.46.39.80 > 192.168.1.2.59676: Flags [.], seq 305454063:305455503, ack 2463422630, win 776, length 1440: HTTP: HTTP/1.1 200 OK
18:57:41.730710 IP 192.168.1.2.59676 > 103.235.46.39.80: Flags [.], ack 305455503, win 4073, length 0
18:57:41.731046 IP 103.235.46.39.80 > 192.168.1.2.59676: Flags [P.], seq 305455503:305456844, ack 2463422630, win 776, length 1341: HTTP
18:57:41.731117 IP 192.168.1.2.59676 > 103.235.46.39.80: Flags [.], ack 305456844, win 4075, length 0
//四次挥手
18:57:41.731595 IP 192.168.1.2.59676 > 103.235.46.39.80: Flags [F.], seq 2463422630, ack 305456844, win 4096, length 0
18:57:41.814116 IP 103.235.46.39.80 > 192.168.1.2.59676: Flags [F.], seq 305456844, ack 2463422631, win 776, length 0
18:57:41.814563 IP 103.235.46.39.80 > 192.168.1.2.59676: Flags [.], ack 2463422631, win 776, length 0
18:57:41.814763 IP 192.168.1.2.59676 > 103.235.46.39.80: Flags [.], ack 305456845, win 4096, length 0

18:57:41.814978 IP 192.168.1.2.59676 > 103.235.46.39.80: Flags [.], ack 305456845, win 4096, length 0
18:57:41.898743 IP 103.235.46.39.80 > 192.168.1.2.59676: Flags [R], seq 305456845, win 0, length 0
```




