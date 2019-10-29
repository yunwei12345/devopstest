

#### 快速安装（docker版）



1   下载镜像包

   ​               

```
ocker pull prom/node-exporter   #  该镜像用于主机系统数据的收集
docker pull prom/prometheus
docker pull grafana/grafana
```



2   启动node-exporter



```
docker run -d -p 9100:9100 \
  -v "/proc:/host/proc:ro" \
  -v "/sys:/host/sys:ro" \
  -v "/:/rootfs:ro" \
    prom/node-exporter
```



3   检查9100端口是否启动

​      

```
root@ubuntu:~# netstat -anpt
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      1147/sshd       
tcp        0     36 192.168.91.132:22       192.168.91.1:63648      ESTABLISHED 2969/0          
tcp        0      0 192.168.91.132:22       192.168.91.1:63340      ESTABLISHED 1321/1          
tcp6       0      0 :::9100                 :::*                    LISTEN      3070/node_exporter

```



4      访问 url ​    

```
http://192.168.91.132:9100/metrics   # 此处为收集到的数据，有了它可以做数据展示
```

![1572324805175](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1572324805175.png)

