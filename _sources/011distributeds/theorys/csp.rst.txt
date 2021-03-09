.. _csp:

并发相关-CSP
###############

* Communicating Sequential Processes
* 通信顺序进程，又翻译为交换消息的顺序程序，用来描述并发性系统的交互模式
* 早在上个世纪七十年代，多核处理器还是一个科研主题，并没有进入普通程序员的视野。 Tony Hoare 于 1977 年提出通信顺序进程（CSP）理论，遥遥领先与他所在的时代。



CSP有以下三个特点::

    1.每个程序是为了顺序执行而创建的
    2.数据通过管道来通信，而不是通过共享内存
    3.通过增加相同的程序来扩容
    // Golang的并发模型基于CSP理论，Golang并发的口号是：不用通过共享内存来通信，而是通过通信来共享内存

Golang并发模式支持并发的元素集::

    goroutines
    channels
    select
    sync package
    // 其中goroutines，channels和select 对应于实现CSP理论，即通过通信来共享内存
    // 这几乎能解决Golang并发的90%问题，另外的10%场景需要通过同步原语来解决，即sync包相关的结构






参考
====

* `Golang 高效实践之并发实践channel篇 <https://www.cnblogs.com/makelu/p/11205704.html>`_
* `【知乎】如何深入浅出地解释并发模型中的 CSP 模型？ <https://www.zhihu.com/question/26192499>`_
* `并发之痛 Thread，Goroutine，Actor <http://jolestar.com/parallel-programming-model-thread-goroutine-actor/>`_

