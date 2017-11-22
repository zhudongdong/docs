
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

<!--stackedit_data:
eyJoaXN0b3J5IjpbNDQyMjgxNDg3XX0=
-->