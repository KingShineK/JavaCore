<h3 style="padding-bottom:6px; padding-left:20px; color:#ffffff; background-color:#E74C3C;">Redis单线程模型为啥这么快？</h3>

**1.基于内存操作:** Redis将所有需要存储的数据都存放在内存中，基于内存的随机访问速度是磁盘的10万倍左右，即使是SSD遥不可及。这是Redis操作快速的重要基础。



**2.C语言实现:** 相同逻辑下的C语言程序，执行效率要比其他语言的高很多。C语言与当前主流的操作系统之间有着独特的关系，抛开开发难度来看，执行速度还是蛮快的。



**3.独特的数据结构:** 



**4.I/O多路复用模型:** 



**5.单线程模型:** 线程不仅在启动和销毁的过程中消耗资源，而且多线程在上下文切换时也会消耗资源。大量的资源都消耗在不必要的“抢占”和“争夺”过程中，不利于高效率操作。单线程正是避免了这种情况