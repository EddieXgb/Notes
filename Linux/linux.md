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









