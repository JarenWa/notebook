<p align="center">
   <a style="font-size:30px;"> synchronized </a>

</p>

# 问题

Synchronized可以作用在哪里? 分别通过对象锁和类锁进行举例。Synchronized本质上是通过什么保证线程安全的? 分三个方面回答：加锁和释放锁的原理，可重入原理，保证可见性原理。Synchronized由什么样的缺陷? Java Lock是怎么弥补这些缺陷的。Synchronized和Lock的对比，和选择?Synchronized在使用时有何注意事项?Synchronized修饰的方法在抛出异常时,会释放锁吗?多个线程等待同一个Synchronized锁的时候，JVM如何选择下一个获取锁的线程?Synchronized使得同时只有一个线程可以执行，性能比较差，有什么提升的方法?我想更加灵活的控制锁的释放和获取(现在释放锁和获取锁的时机都被规定死了)，怎么办?什么是锁的升级和降级? 什么是JVM里的偏斜锁、轻量级锁、重量级锁?不同的JDK中对Synchronized有何优化?



# 1 Java 是如何解决线程的安全问题的？使用线程的同步机制。

方式1：同步代码块

synchronized(同步监视器){
    //需要被同步的代码
}

synchronized好处：解决了线程的安全问题。

弊端：在操作共享数据时，多线程其实是串行执行的，意味着性能低。

<br>

# 2 
## 2.1 


# Reference