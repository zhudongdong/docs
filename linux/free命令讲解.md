# free命令命令详解

参考[free命令解析](http://cizixs.com/2015/10/01/linux-memory-management-through-free)


```shell
xxx@xxx:~$ free
             total       used       free     shared    buffers     cached
Mem:        374256     330952      43304          0      14400     238128
-/+ buffers/cache:      78424     295832
Swap:       786428       2224     784204
```

第一行 
```shell
total       used       free     shared    buffers     cached
```
>- total：os实际物理内存大小
>- used：os实际使用的物理内存大小
>- free：os空闲物理内存大小
>- shared：共享物理内存大小，进程间共享使用
>- buffers：缓冲使用大小，后面讲解
>- cached：缓存使用大小，后面讲解

其中
>- total = used + free

第二行，代表应用程序实际使用的内存
```shell
-/+ buffers/cache:      78424     295832
```

>- 前一个值表示 - buffers/cached，即 used - buffers/cached，表示应用程序实际使用的内存

>- 后一个值表示 + buffers/cached，即 free + buffers/cached，表示理论上都可以被使用的内存

第三行，表示 swap 的使用情况：总量、使用的和未使用的。

## buffer
os写文件时，由于磁盘的速度较慢，为了提升应用程序的‘写’速度，会先将数据写入buffer，之后会从buffer中取出数据再写入磁盘，通过buffer变相提升了磁盘的速度。

使用U盘时拷贝数据时，通常os提示写完成后，弹出U盘时会提示U盘依然在使用就是由于buffer的原因。
## cache
os读文件时，由于磁盘的速度较慢，会将文件数据先读入cache，之后这部分数据的重复读取都走cache，提升了读性能。

清空cache：
```shell
echo 1 > /proc/sys/vm/drop_caches
```
## swap
swap 是实现虚拟内存的重要概念。如果系统的负载太大，内存被用完，可能会出现严重的问题。swap 就是把硬盘上一部分空间当做内存使用，正在运行程序会使用物理内存，把没有正在使用的内存放到硬盘，这叫做 swap out；而把硬盘 swap 部分的内存重新放到物理内存中，叫做 swap in。

swap 可以再逻辑上扩大内存空间，但是会造成系统变慢，因为硬盘读写速度很慢。linux 系统比较智能，会把那些不怎么频繁使用的内存放到 swap。
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTQ1NzM1Njc2NiwtMjEyMDU0MjA1XX0=
-->