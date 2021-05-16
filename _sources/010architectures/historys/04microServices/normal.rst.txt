常用
####

Wikipedia::

    Microservices is a software development technique 
    — a variant of the service-oriented architecture （SOA） structural style.

    维基百科上，人们仍然是把微服务定义成了 SOA 的一个变种

2012 年，在波兰克拉科夫举行的 “33rd Degree Conference” 大会上，Thoughtworks 首席咨询师 James Lewis 做了题为 `《Microservices - Java, the Unix Way》 <http://2012.33degree.org/talk/show/67>`_ 的主题演讲::

    单一服务职责、康威定律、自动扩展、领域驱动设计等原则
    未提 SOA，反而号召大家，应该重拾 Unix 的设计哲学（As Well Behaved Unix Services）

微服务真正崛起是在 2014 年。相信我们大多数程序员，也是从 Martin Fowler 和 James Lewis 合写的文章  `“Microservices: a definition of this new architectural term” <https://martinfowler.com/articles/microservices.html>`_ 里面::

    这篇文章虽然不是最早提出 “微服务” 这个概念的，但却是真正丰富的、广为人知的和可操作的微服务指南。
    也就是说，这篇文章才是微服务的真正起源。

    定义了现代微服务的概念：
    微服务是一种通过多个小型服务的组合，来构建单个应用的架构风格，这些服务会围绕业务能力而非特定的技术标准来构建。
    各个服务可以采用不同的编程语言、不同的数据存储技术、运行在不同的进程之中。
    服务会采取轻量级的通讯机制和自动化的部署机制，来实现通讯与运维。

优点::

    提升开发速度，每个服务足够内聚，足够小，代码容易理解；
    服务独立测试、部署、升级、发布；
    按需定制的 DFX，提高资源利用率
        每个服务可以各自进行 x 扩展和 z 扩展，而且，每个服务可以根据自己的需要部署到合适的硬件服务器上
        每个服务按需要选择 HA 的模式，选择接受服务的实例个数；
    容易扩大开发团队
        可以针对每个服务（service）组件开发团队
    提高容错性（fault isolation）
        一个服务的内存泄露并不会让整个系统瘫痪
        新技术的应用，系统不会被长期限制在某个技术栈上


缺点::

    没有银弹，微服务提高了系统的复杂度
    开发人员要处理分布式系统的复杂性
    服务之间的分布式通信问题
    服务的注册与发现问题
    服务之间的分布式事务问题
    数据隔离再来的报表处理问题
    服务之间的分布式一致性问题
    服务管理的复杂性，服务的编排
    不同服务实例的管理

微服务的三维扩展模型
====================

.. figure:: /images/microservices/microservice_3d_model.png

   微服务的三维扩展模型



Chris Richardson 提出的微服务的三维扩展模型::

    X 轴，服务实例水平扩展，保证可靠性与性能
    Y 轴，功能的扩展，服务单一职责，功能独立
    Z 轴，数据分区，数据独立，可靠性保证


通信问题::

    第一个维度是一对一还是一对多:
      一对一：每个客户端请求有一个服务实例来响应。
      一对多：每个客户端请求有多个服务实例来响应。

    第二个维度是这些交互式同步还是异步:
      同步模式：客户端请求需要服务端即时响应，甚至可能由于等待而阻塞。
      异步模式：客户端请求不会阻塞进程，服务端的响应可以是非即时的。

            一对一                   一对多
    同步    Request/Response         --
    异步    Notification             Publish/suscribe
           Request/async response    Publish/async responses



.. figure:: /images/microservices/deployment.jpg

   服务发布体系











