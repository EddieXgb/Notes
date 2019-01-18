# linux命令

##端口：

__查看端口被哪个进程占用：__

```lsof -i:8000
lsof -i:8000
```

__查看端口进程状态：__

```
netstat -tunlp |grep 8000
```

[点这里](<https://www.cnblogs.com/wangtao1993/p/6144183.html>)

## linux防火墙：

___临时生效，重启后复原___

__开启：__

```
service iptables start
```

__关闭：__

```
service iptables stop
```

___永久性生效，重启后不会复原___

__开启：__

```
chkconfig iptables on
```

__关闭：__

```
chkconfig iptables off
```

__重启防火墙：__

```
service iptables restart
```



## Ubuntu防火墙

__关闭防火墙开机自启：__

```
ufw disable
```

__开启防火墙开机自启：__

```
ufw enable
```

##redhat，centos6及fedora旧的版本防火墙：

__防火墙状态：__

```
service iptables status
```

| 命令                      | 作用               |
| ------------------------- | ------------------ |
| service iptables start    | 开启防火墙         |
| service iptables stop     | 关闭防火墙         |
| service iptables status   | 查看防火墙状态     |
| chkconfig iptables on     | 防火墙开机自启     |
| chkconfig iptables off    | 禁止开机自启       |
| chkconfig iptables status | 查看是否为开机自启 |

## 文件操作：

__查询当前目录下文件大小:__

```
du -sh * | sort -n
```

__删除符合查询条件的文件：__

```
find . -name "*.log" | xargs rm -rf
```



## 通道状态

```
netstat -n | awk '/^tcp/ {++S[$NF]} END {for(a in S) print a, S[a]}'  
```

### 解决服务器大量time_wait,服务器优化方案

__修改/etc/sysctl.conf__

```
#对于一个新建连接，内核要发送多少个 SYN 连接请求才决定放弃,不应该大于255，默认值是5，对应于180秒左右时间   
net.ipv4.tcp_syn_retries=2  
#net.ipv4.tcp_synack_retries=2  
#表示当keepalive起用的时候，TCP发送keepalive消息的频度。缺省是2小时，改为300秒  
net.ipv4.tcp_keepalive_time=1200  
net.ipv4.tcp_orphan_retries=3  
#表示如果套接字由本端要求关闭，这个参数决定了它保持在FIN-WAIT-2状态的时间  
net.ipv4.tcp_fin_timeout=30    
#表示SYN队列的长度，默认为1024，加大队列长度为8192，可以容纳更多等待连接的网络连接数。  
net.ipv4.tcp_max_syn_backlog = 4096  
#表示开启SYN Cookies。当出现SYN等待队列溢出时，启用cookies来处理，可防范少量SYN攻击，默认为0，表示关闭  
net.ipv4.tcp_syncookies = 1  
  
#表示开启重用。允许将TIME-WAIT sockets重新用于新的TCP连接，默认为0，表示关闭  
net.ipv4.tcp_tw_reuse = 1  
#表示开启TCP连接中TIME-WAIT sockets的快速回收，默认为0，表示关闭  
net.ipv4.tcp_tw_recycle = 1  
  
##减少超时前的探测次数   
net.ipv4.tcp_keepalive_probes=5   
##优化网络设备接收队列   
net.core.netdev_max_backlog=3000 

修改完之后执行/sbin/sysctl -p让参数生效
```

## 服务器大量close_wait，问题主要在程序里

[HttpClient4.X 升级 入门 + http连接池使用](<https://blog.csdn.net/shootyou/article/details/6415248>)



##jstack-查看Java进程的线程堆栈信息，锁定高消耗资源代码

```
##找出该进程内最耗费CPU的线程
top -Hp pid

##得到16进制值
printf "%x\n" 21553

jstack pid | grep 16进制值 
```

