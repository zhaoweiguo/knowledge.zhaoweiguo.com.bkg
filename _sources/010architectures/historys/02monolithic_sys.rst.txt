单体系统时代
############

“单体” 这个名称，却是从微服务开始流行之后，才 “事后追认” 所形成的概念。


思维误区: 单体架构是落后的系统架构风格，最终会被微服务所取代。

.. note:: 进程间通讯：Inter-Process Communication，IPC。RPC 属于 IPC 的一种特例


.. note:: 当我们在讨论单体系统的缺陷的时候，必须基于软件的性能需求超过了单机，软件的开发人员规模明显超过了 “2 Pizza Teams” 范畴的前提下，这样才有讨论的价值。


单体系统::

    Monolith means composed all in one piece. 
    The Monolithic application describes a single-tiered software application 
        in which different components combined into a single program from a single platform.
    —— Monolithic Application，Wikipedia


    分层架构（Layered Architecture）
    横向扩展（Scale Horizontally）

缺点::

    单体系统的真正缺陷实际上并不在于要如何拆分，而在于拆分之后，它会存在隔离与自治能力上的欠缺。

    如果在单体架构中，有任何一部分的代码出现了缺陷，过度消耗进程空间内的公共资源，那所造成的影响就是全局性的、难以隔离的。

    由于隔离能力的缺失，除了会带来难以阻断错误传播、不便于动态更新程序的问题，还会给带来难以技术异构等困难。

技术异构::

    马丁・福勒（Martin Fowler）提出的 9 个特征，技术异构就是其中之一。
    它的意思是说允许系统的每个模块，自由选择不一样的程序语言、不一样的编程框架等技术栈去实现。


一个需要权衡的问题::

    如果说共享同一进程获得简单、高效这些优势的代价，是损失了各个功能模块的自治、隔离能力，那这两者孰轻孰重呢？


微服务去代替单体系统的根本原因。我认为最根本的原因是：单体系统并不兼容 “Phoenix” 的特性

随着软件架构的不断演进，我们构﻿建可靠系统的观念，开始从 “追求尽量不出错”，转变为了正视 “出错是必然”的。









