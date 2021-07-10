
### Unix 关闭查看端口、杀死进程
查找8080端口：

```sudo lsof -i :8080```

根据PID杀进程：

```sudo kill -9 pid（对应的pid号）```