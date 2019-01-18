__查看java进程__

`jps -l`

__每隔1000行打印一次或导出GC状态__

```
jstat -gc pid 1000 或者 jstat -gc pid 1000 > out.txt

S0C S0U：Survivor 0区的大小及使用情况
S1C S1U：Survivor 1区的大小及使用情况
EC EU：Eden 区的大小及使用情况
OC OU：Old 区的大小及使用情况
PC PU：Perm 区的大小及使用情况（Java 8 中取消）
MC MU：Metaspace 区的大小及使用情况（Java 8 中用户替代 Perm 区）
YGC YGCT：Young Generation Minor GC 的数目及时间
FGC FGCT：Old Generation Full GC 的数目及时间
GCT：GC 总时间 = YGCT + FGCT
```

__打印或导出堆内存使用情况__

```
jmap -heap pid 或者 jmap -heap pid > out.txt

Heap Configuration 堆的配置
Heap Usage 对的使用情况，包括 Eden 区, From 区，To 区，Old 区，Perm 区（Java 8 中取消）
```

__打印或导出堆内存中对象的数量及大小__

```
jmap -histo pid 或者 jmap -histo pid > out.txt

class name 类的名称
instances 类对应的对象的数目
bytes 类对应的对象的大小
```

[更多](<https://www.cnblogs.com/lizhonghua34/p/7307139.html>)

