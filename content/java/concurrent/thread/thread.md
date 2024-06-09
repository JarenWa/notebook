<p align="center">
   <a style="font-size:30px;"> 线程 </a>

</p>

<p align="center">
   <a href=" " target="_blank"> Demo </a>
</p>

# 带着BAT大厂的面试问题去理解
多线程的出现是要解决什么问题的?线程不安全是指什么? 举例说明并发出现线程不安全的本质什么? 可见性，原子性和有序性。Java是怎么解决并发问题的? 3个关键字，JMM和8个Happens-Before线程安全是不是非真即假? 不是线程安全有哪些实现思路?如何理解并发和并行的区别




## 线程启用方法
实现 Runnable 接口；
实现 Callable 接口；
继承 Thread 类。

实现 Runnable 和 Callable 接口的类只能当做一个可以在线程中运行的任务，不是真正意义上的线程，因此最后还需要通过 Thread 来调用。可以说任务是通过线程驱动从而执行的。


## 实现 Runnable 接口



## 实现 Callable 接口
## 继承 Thread 类


<br>

# 2 
## 2.1 


# Reference