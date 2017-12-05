### 一、什么是load average
linux系统中的Load对当前CPU工作量的度量。

 (WikiPedia: the system load is a measure of the amount of work that a computer system is doing)。

也有简单的说是进程队列的长度。Load Average 就是一段时间 (1 分钟、5分钟、15分钟) 内平均 Load 。
 
 我们可以通过系统命令"w"查看当前load average情况
```shell
    [root@CNC-BJ-5-3N1 ~]# w
20:01:55 up 76 days, 8:20, 6 users, load average: 1.30, 1.48, 1.69
```
这三个值分别表示近1分钟、5分钟、15分钟的cpu负载。

linux系统是5秒钟进行一次Load采样

---

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE4NTUzNTU2MDRdfQ==
-->