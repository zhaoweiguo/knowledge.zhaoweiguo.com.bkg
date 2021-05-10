云原生
######

定义
====

Pivotal最初的定义::

    早在2015年Pivotal公司的Matt Stine写了一本叫做迁移到云原生应用架构的小册子，
    其中探讨了云原生应用架构的几个主要特征：

    符合12因素应用
    面向微服务架构
    自服务敏捷架构
    基于API的协作
    抗脆弱性


CNCF最初的定义::

    到了2015年Google主导成立了云原生计算基金会（CNCF）
    起初CNCF对云原生（Cloud Native）的定义包含以下三个方面：

    1. 应用容器化
    2. 面向微服务架构
    3. 应用支持容器的编排调度


CNCF对云原生的重新定义（中英对照）::

    Cloud native technologies empower organizations to build and run 
        scalable applications in modern, dynamic environments such as 
            public, private, and hybrid clouds. 
    Containers, service meshes, microservices, immutable infrastructure, 
        and declarative APIs exemplify this approach.
    云原生技术有利于各组织在公有云、私有云和混合云等新型动态环境中，构建和运行可弹性扩展的应用。
    云原生的代表技术包括容器、服务网格、微服务、不可变基础设施和声明式API。

    These techniques enable loosely coupled systems that are 
        resilient, manageable, and observable. 
    Combined with robust automation, they allow engineers to make high-impact changes 
        frequently and predictably with minimal toil.
    这些技术能够构建容错性好、易于管理和便于观察的松耦合系统。
    结合可靠的自动化手段，云原生技术使工程师能够轻松地对系统作出频繁和可预测的重大变更。

    The Cloud Native Computing Foundation seeks to drive adoption of this paradigm 
        by fostering and sustaining an ecosystem of open source, vendor-neutral projects. 
    We democratize state-of-the-art patterns to make these innovations accessible for all.
    云原生计算基金会（CNCF）致力于培育和维护一个厂商中立的开源生态系统，来推广云原生技术。
    我们通过将最前沿的模式民主化，让这些创新为大众所用。


* 参考: https://jimmysong.io/kubernetes-handbook/cloud-native/cloud-native-definition.html
* CNCF Cloud Native Definition v1.0 - github.com: https://github.com/cncf/toc/blob/master/DEFINITION.md

云原生的设计哲学
================

云原生思想的2个理论基础::

    1. 不可变基础理论: 目前实现-容器镜像
    2. 云应用编排理论: 目前实现-容器设计模式

* 云原生本身甚至不能称为是一种架构，它首先是一种基础设施，运行在其上的应用称作云原生应用，只有符合云原生设计哲学的应用架构才叫云原生应用架构。
* 就像云改变了业务和基础设施之间的关系一样，云原生应用程序也改变了应用程序和基础设施之间的关系。

云原生系统的设计理念如下(很多都是继承自分布式应用的设计理念)::

    面向分布式设计（Distribution）：容器、微服务、API 驱动的开发；
    面向配置设计（Configuration）：一个镜像，多个环境配置；
    面向韧性设计（Resistancy）：故障容忍和自愈；
    面向弹性设计（Elasticity）：弹性扩展和对环境变化（负载）做出响应；
    面向交付设计（Delivery）：自动拉起，缩短交付时间；
    面向性能设计（Performance）：响应式，并发和资源高效利用；
    面向自动化设计（Automation）：自动化的 DevOps；
    面向诊断性设计（Diagnosability）：集群级别的日志、metric 和追踪；
    面向安全性设计（Security）：安全端点、API Gateway、端到端加密；

收集
====

试想，如果未来的应用开发，开发者通过函数计算、弹性容器服务等能力去承载自己的业务逻辑，存储、数据库、消息等中间件能力通过 Backend as a Service 的方式去获取，即未来使用云计算的开发者能够无需关心云计算的基础底层概念，直接聚焦自己的业务开发，以近乎无感的方式获得云计算的帮助。


不可变基础设施指的是应用的基础设施应是不可变的，是一个自包含、自描述可以完全在不同环境中迁移的东西，容器技术正是这一理念实现的基石。



代理和网关有什么区别
====================

* 代理和网关有什么区别: https://github.com/xianshannan/interview/issues/27

代理::

    代理（英语：Proxy）也称网络代理，是一种特殊的网络服务，
        允许一个网络终端（一般为客户端）通过这个服务与另一个网络终端（一般为服务器）进行非直接的连接。

.. note:: 一般认为代理服务有利于保障网络终端的隐私或安全，防止攻击。


网关::

    在计算机网络中，网关（英语：Gateway）是转发其他服务器通信数据的服务器，
        接收从客户端发送来的请求时，它就像自己拥有资源的源服务器一样对请求进行处理。
        有时客户端可能都不会察觉，自己的通信目标是一个网关。

    网关也经常指把一种协议转成另一种协议的设备，比如语音网关。

.. note:: 现在的网关很多情况下都是对外提供 HTTP 协议进行通信，内部是非 HTTP 协议通信。

这里的区别都是严格意义上来说的::

    代理服务器可以做任何信息过滤，但是网关不会。
    代理的协议不会转变，但是网关一般都会转换协议，所以网关也相对安全。

* 代理，网关，隧道，有什么区别与联系: https://www.zhihu.com/question/268204483

根据 RFC2616 标准，对 HTTP 协议来说::

    1. 代理是被视为通信的参与方，是对双方透明的一个中间方而且可以改写用户 / 服务器所发出的请求 / 回复。
    2. 而网关则是一个回复用户请求的服务端代理人，对用户来说是完全不透明的，
        可能的职责之一是将用户的请求翻译成其他协议理解的形式，比如说 nginx->Apache。
    3. 隧道是一个盲目转发的代理（不改变任何请求 / 回复内容），
       在启用后对 HTTP 协议来说完全不透明，标准中指出隧道的使用是为了跨越防火墙或者其他障碍。 
       一个关键的区别在于隧道不允许缓存用户请求和服务器回复。




参考
====

* :ref:`Serverless<serverless>`








