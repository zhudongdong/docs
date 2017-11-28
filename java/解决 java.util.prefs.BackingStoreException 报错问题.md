# 解决 java.util.prefs.BackingStoreException 报错问题


今天应用持续如下异常信息：

```java
WARNING: Could not lock System prefs. Unix error code 7.
Nov 28, 2017 8:56:38 AM java.util.prefs.FileSystemPreferences syncWorld
WARNING: Couldn't flush system prefs: java.util.prefs.BackingStoreException: Couldn't get file lock.
Nov 28, 2017 8:57:08 AM java.util.prefs.FileSystemPreferences checkLockFile0ErrorCode

```

我在本地并没有找到java.util.prefs.FileSystemPreferences这个类，后来找到了网上的一片文章，[http://blog.csdn.net/u011700281/article/details/50052363](http://blog.csdn.net/u011700281/article/details/50052363)
也参照了IBM的文章 [http://www-01.ibm.com/support/docview.wss?uid=swg21515420](http://www-01.ibm.com/support/docview.wss?uid=swg21515420)

## 解决办法
>- 1、给当前用户创建home目录或
>- 2、给当前用户赋权或
>- 3、删除/etc/.java 目录或
>- 4、使用root启动或
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTgyOTcyODQzN119
-->