# ANR

## 1. ANR的四种场景

* Service TimeOut: service 未在规定时间执行完成：前台服务 20s，后台 200s

* BroadCastQueue TimeOut: 未在规定时间内未处理完广播：前台广播 10s 内, 后台 60s 内

* ContentProvider TimeOut: publish 在 10s 内没有完成

* Input Dispatching timeout: 5s 内未响应键盘输入、触摸屏幕等事件

我们可以看到， Activity 的生命周期回调的阻塞并不在触发 ANR 的场景里面，所以并不会直接触发 ANR。

只不过死循环阻塞了主线程，如果系统再有上述的四种事件发生，就无法在相应的时间内处理从而触发 ANR。

## 2. 哪些操作会导致ANR

在主线程执行以下操作：
1. 高耗时的操作，如图像变换
2. 磁盘读写，数据库读写操作
3. 大量的创建新对象

## 3. 如何避免

1. UI线程尽量只做跟UI相关的工作
2. 耗时的操作(比如数据库操作，I/O，连接网络或者别的有可能阻塞UI线程的操作)把它放在单独的线程处理
3. 尽量用Handler来处理UIThread和别的Thread之间的交互
