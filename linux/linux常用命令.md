
[toc]
### 查看cpu信息
>cat /proc/cpuinfo
 - processor       逻辑处理器的id。`
 - physical id    物理封装的处理器的id。
 - core id        每个核心的id。
 - cpu cores      位于相同物理封装的处理器中的内核数量。
 - siblings       位于相同物理封装的处理器中的逻辑处理器的数量。

#### 物理CPU的个数
> cat /proc/cpuinfo |grep "physical id" |sort -u |wc -l
####逻辑CPU的个数
> cat /proc/cpuinfo |grep "processor"| wc -l
####CPU是几核
> cat /proc/cpuinfo |grep "cores"|uniq
####CPU的主频
> cat /proc/cpuinfo |grep MHz|uniq 
####查看当前操作系统内核信息
> uname -a

#### 查看内存信息
>free

### 查看网卡信息
#### 网卡速度
>ethtool eth0  
#### 网络接口队列数
>cat /proc/interrupts | grep eth0


### 查看文件句柄数
>ulimit -n 每个进程允许打开句柄的最大数

> cat /proc/sys/fs/file-nr 
```shell

```

ulimit is a per process limit and you can increase or decrease it. Also the /proc/sys/fs/file-max tells the maximum open file descriptors allowed by the kernel. 

Ok now if you see /proc/sys/fs/file-nr, the first column show number of current open file descriptors and the third column show the total allowed file descriptors which is equal to /proc/sys/fs/file-max. But lsof | wc -l will show you more number then that in the first column, that is because lsof will also list files without a file discreptor(e.g. you may see a lot of memory maped library files). To check this try lsof | wc -l | grep 4893 (where 4893 is pid of some process just taken for example), now check for the same pid in /proc/4893/fd. You will see the difference. Also if you want, you can set the /proc/sys/fs/file-max as follows. 
e.g. echo "12227" > /proc/sys/fs/file-max.
I think it is much clear now.
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTQ2NjYwNjA2Nl19
-->