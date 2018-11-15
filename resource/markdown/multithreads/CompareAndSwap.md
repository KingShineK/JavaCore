<h3 style="padding-bottom:6px; padding-left:20px; color:#ffffff; background-color:#E74C3C;">CAS实现原理</h3>

> **CAS** 是 **CompareAndSwap** 的缩写，意思是 **比较** 并 **交换**。	它是无锁化的实现是经典的乐观锁。
>
> **CAS** 操作很简单，它包含三个操作数：**内存地址V**、**预期原值A**、**新值B**。先比较内存地址V处的值与预期原值A是否相等，如果相等就将内存地址V处更新为新值B。在配合循环使用时，若CAS操作失败，会循环执行或到达某个终止处。此操作配合 **循环** 使用时，又称为 **自旋锁** 的实现方式。



<h3 style="padding-bottom:6px; padding-left:20px; color:#ffffff; background-color:#E74C3C;">CAS存在的问题</h3>

#### 1、ABA的问题

> 比如一个线程操作时，先将内存地址V处的值A更新为值B，然后又将值B更新为值A。最后CAS判断内存地址V处的没有变化，认为操作更新未成功，但实质上是已经更新过了。这就是经典的 **ABA问题**。

**解决方法**：

①加时间戳：

**②加版本号**：



#### 2、循环开销大

> **CAS** 这种也是乐观锁，如果线程较多、资源抢占激烈、命中率低的情况下，不断的循环会不断的消耗资源。实现上，可以设置最大循环数，达到最大循环数还没有占有资源就自动放弃，避免无限的循环。



#### 3、最多只能保证一个共享变量的操作

> CAS 最多只能操作一个共享变量，单体效率低。