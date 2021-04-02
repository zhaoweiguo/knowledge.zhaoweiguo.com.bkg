REST
##########

* “表征状态转移”（Representational State Transfer）

* 面向过程编程时，以算法和处理过程为中心，输入数据，输出结果。为了符合计算机世界中主流的交互方式。
* 面向对象编程时，将数据和行为统一起来、封装成对象。为了符合现实世界的主流交互方式。
* 面向资源编程时，将数据（资源）作为抽象的主体，把行为看作是统一的接口。为了符合网络世界的主流的交互方式::
  
    把问题空间中的数据对象作为抽象的主体，
    把解决问题时从输入数据到输出结果的处理过程，看作是一个（组）数据资源的状态不断发生变换而导致的结果

    面向资源编程是符合目前网络主流的交互方式，
    也因此 REST 常常被看作是为基于网络的分布式系统量身定做的交互方式。

.. note:: 对于这种存在争议性大的东西，尽可能的少引入团队，争议性大就意味着大家对他的理解的共性越少，无论是引入推广还是实施的具体效果都会存在很长周期的磨合与统一。引入它带来认知负荷的提高，弊端就很可能完全盖过了收益。




与RPC对比
=========

.. note:: 无论是『思想』上、『概念』上，还是使用范围上，REST 与 RPC 都不完全一样，它们在本质上并不是同一个类型的东西，充其量只算是有一些相似，在应用中会有一部分功能重合的地方。

『思想』上::

    REST 与 RPC 在思想上存在差异的核心，是抽象的目标不一样，
    也就是『面向资源』的编程思想与『面向过程』的编程思想之间的区别。


『概念』上::

    REST 并不是一种协议:
    因为协议都带有一定的规范性和强制性，最起码也该有个规约文档，
    比如 JSON-RPC，它哪怕再简单，也要有个《JSON-RPC Specification》来规定协议的格式细节、异常、响应码等信息。
    但是 REST 并没有定义这些内容，虽然它有一些指导原则，但实际上并不受任何强制的约束。


.. note:: 在『使用范围』上，REST 与 RPC 作为主流的两种远程调用方式，在使用上确实有重合之处，但重合的区域有多大就见仁见智了。


『使用范围』上::

    从RPC 的3个典型发展方向来对比RPC和REST:
    1. 分布式对象
      与 REST 毫无关系

    2. 提升调用效率
      a. REST 应用得最多是供「浏览器端」消费的远程服务:
      因为以浏览器作为前端，对于传输协议、序列化器这两点都没有什么选择权
      想要更高效率也有心无力。

      b. 在移动端、桌面端或者分布式服务端的节点之间通讯这一块:
      使用 REST 的前提是网络没有成为性能上的瓶颈。
      但是在需要追求传输效率的场景里，REST 提升传输效率的潜力有限

    3. 简化调用复杂性
      在众多 RPC 里，也就 JSON-RPC 有机会与 REST 竞争
      其他 RPC 协议与框架:
          哪怕是能够支持 HTTP 协议，
          哪怕提供了 JavaScript 版本的客户端（如 gRPC-Web）
          也只是具备前端使用的理论可行性，很少能看到有实际项目把它们真的用到浏览器上的


.. note:: 尽管有着种种不同，REST 跟 RPC 还是产生了很频繁的比较与争论，这两种分别面向资源和面向过程的远程调用方式，就像当年面向对象与面向过程的编程思想一样，非得分出个高低不可。


REST概念
========

REST 概念的提出来自于罗伊・菲尔丁（Roy Fielding）在 2000 年发表的博士论文: `《Architectural Styles and the Design of Network-based Software Architectures》(架构风格与网络的软件架构设计) <https://www.ics.uci.edu/~fielding/pubs/dissertation/top.htm>`_ 。中文版参见 `这儿 <https://www.infoq.cn/article/2007/07/dlee-fielding-rest/>`_

罗伊・菲尔丁（Roy Fielding）简介::

    是一名很优秀的软件工程师
    是 Apache 服务器的核心开发者，后来成为了著名的 Apache 软件基金会的联合创始人
    是 HTTP 1.0 协议（1996 年发布）的专家组成员
    是 HTTP 1.1 协议（1999 年发布）的负责人
        指导设计 HTTP 1.1 协议的理论和思想，最初是以备忘录的形式，在专家组成员之间交流，
        这个备忘录其实就是 REST 的雏形。

.. note:: 什么叫『表征状态转移』？即什么是REST(Representational State Transfer)。

Fielding 在提出 REST 时，所谈论的范围是 “架构风格与网络的软件架构设计”（Architectural Styles and Design of Network-based Software Architectures），而不是现在被人们所狭义理解的一种 “远程服务设计风格”。Fielding 提的 REST 是更通用的一种设计理念

超文本(Hypertext)
-----------------

.. note:: 先去理解什么是 HTTP，再配合一些实际例子来进行类比，你就会发现 “REST” 实际上是 “HTT”（Hyper Text Transfer，超文本传输）的进一步抽象，它们就像是接口与实现类之间的关系。

.. note:: HTTP 中使用的 “超文本” 一词，是美国社会学家泰德・H・尼尔森（Theodor Holm Nelson）在 1967 年于`《Brief Words on the Hypertext》 <https://archive.org/details/SelectedPapers1977>`_ 一文里提出的

Nelson在 1992 年修正后的定义::

    By now the word "hypertext" has become generally accepted for branching and responding text, 
    but the corresponding word "hypermedia", meaning complexes of 
        branching and responding graphics, movies and sound – as well as text – is much less used. 
    Instead they use the strange term "interactive multimedia": 
        this is four syllables longer, and does not express the idea of extending hypertext.
    —— Theodor Holm Nelson Literary Machines, 1992

    “超文本（或超媒体）” 指的是一种 “能够对操作进行判断和响应的文本（或声音、图像等）”


REST 中的关键概念
-----------------

资源（Resource）::

    内容本身（可以将其视作是某种信息、数据），我们称之为 “资源”

表征（Representation）::

    “表征” 这个概念是指信息与用户交互时的表示形式:
    如:
      同一资源:
        服务端向浏览器返回的 HTML 格式的数据
        服务端向浏览器返回的 PDF 格式的数据
        服务端向浏览器返回的 Markdown 格式的数据
        服务端向浏览器返回的 RSS 格式的数据
        ...
      上面就是同一资源的多种表征

状态（State）::

    在特定语境中才能产生的上下文信息就被称为 “状态”，如:
      读完了这篇文章，想再接着看下一篇文章的内容时，你向服务器发出请求 “给我下一篇文章”。
      但是 “下一篇” 是个相对概念，必须依赖 “当前你正在阅读的文章是哪一篇”，这样服务器才能正确回应

    有状态（Stateful）还是无状态（Stateless），都是只相对于服务端来说的:
    1. 服务器记住用户的状态，这是有状态
    2. 客户端来记住状态，在请求的时候明确告诉服务器，这是无状态

转移（Transfer）::

    服务器通过某种方式，把 “用户当前阅读的文章” 转变成 “下一篇文章”，这就被称为 “表征状态转移”

1. 统一接口（Uniform Interface）::

    “统一接口”，包括：GET、HEAD、POST、PUT、DELETE、TRACE、OPTIONS 七种基本操作

    任何一个支持 HTTP 协议的服务器都会遵守这套规定，对特定的 URI 采取这些操作，服务器就会触发相应的表征状态转移。

2. 超文本驱动（Hypertext Driven）::

    浏览器作为通用的客户端，任何网站的导航（状态转移）行为都不可能是预置于浏览器代码之中，
        而是由服务器发出的请求响应信息（超文本）来驱动的。
    这点与其他带有客户端的软件有十分本质的区别，
        在那些软件中，业务逻辑往往是预置于程序代码之中的，
        有专门的页面控制器（无论在服务端还是在客户端中）来驱动页面的状态转移。

3. 自描述消息（Self-Descriptive Messages）::

    一种被广泛采用的自描述方法，是在名为 “Content-Type” 的 HTTP Header 中标识出互联网媒体类型（MIME type）
    比如 “Content-Type : application/json; charset=utf-8”

    互联网媒体类型（MIME type）:
    https://zh.wikipedia.org/wiki/%E4%BA%92%E8%81%94%E7%BD%91%E5%AA%92%E4%BD%93%E7%B1%BB%E5%9E%8B

RESTful 风格的系统六个特征
--------------------------

1. 服务端与客户端分离（Client-Server）::

    分离开用户界面和数据存储所关注的逻辑，有助于提高用户界面跨平台的可移植性。

    不分离的情况如: 原始的jsp, php，服务代码与html混在一起
    风水轮流转:
    由于前端的日渐强势，开始出现前端代码反过来驱动服务端进行渲染的 SSR 技术

2. 无状态（Stateless）::

    这是 REST 的一条关键原则

    REST 希望服务器能不负责维护状态，
    每一次从客户端发送的请求中，应该包括所有必要的上下文信息，会话信息也由客户端保存维护，
    服务器端依据客户端传递的状态信息来进行业务处理，并且驱动整个应用的状态变迁。

    服务端无状态可以在分布式环境中获得很高价值的好处。

    注: 越复杂、越大型的系统越难达到此标准。
      大型系统的上下文状态数量太大，可能客户端在发送请求时，无法全部囊括系统里所有必要的上下文信息。

3. 可缓存（Cacheability）::

    无状态服务，虽然提升了系统的可见性、可靠性和可伸缩性，但也降低了系统的网络性。
      即: 无状态的服务则可能会需要多个请求，或者在请求中带有冗余的信息。
    为缓解这矛盾，REST 希望软件系统能像万维网一样，客户端和中间的通讯传递者（代理）可将部分服务端的应答缓存

    运作良好的缓存机制可以减少客户端、服务器之间的交互，甚至有些场景中可以完全避免交互，这就进一步提高了性能

4. 分层系统（Layered System）::

    客户端一般不需要知道是否直接连接到了最终的服务器，或者是连接到路径上的中间服务器。
    中间服务器可以通过负载均衡和共享缓存的机制，提高系统的可扩展性，这样也便于缓存、伸缩和安全策略的部署。

5. 统一接口（Uniform Interface）::

    REST 希望开发者面向资源编程，
      希望软件系统设计的重点放在抽象系统该有哪些资源上，而不是抽象系统该有哪些行为（服务）上。

    统一接口也是 REST 最容易陷入争论的地方，
      基于网络的软件系统，到底是面向资源更好，还是面向服务更合适，
      这件事情在很长的时间里恐怕都不会有个定论，也许永远都没有。
    但是，有一个已经基本清晰的结论是：面向资源编程的抽象程度通常更高。

    坏处是往往距离人类的思维方式更远
    好处是往往通用程度会更好。

    举例:
      后台管理上的登录、注销功能
    说明:
      面向服务的概念: 登录=>login、注销=>logout
      面向资源的概念: 
          设定一个Session 资源
          登录=> PUT Session
          注销=> DELETE Session

    要在架构设计中合理恰当地利用统一接口，Fielding 给出了三个建议：
      第一，系统要能做到每次请求中都包含资源的 ID，所有操作均通过资源 ID 来进行；
      第二，每个资源都应该是自描述的消息；
      第三，通过「超文本」来驱动应用状态的转移。


6. 按需代码（Code-On-Demand）::

    被 Fielding 列为了一条可选原则
      原因其实并非是它特别难以达到，更多是出于必要性和性价比的实际考虑。

    按需代码是指任何按照客户端（如浏览器）的请求，将可执行的软件程序从服务器发送到客户端的技术。

    例子:
    以前的 Java Applet 技术、今天的 WebAssembly 等都属于典型的按需代码，
    蕴含着具体执行逻辑的代码存放在了服务端，
    只有当客户端请求了某个 Java Applet 之后，
    代码才会被传输并在客户端机器中运行，结束后通常也会随即在客户端中被销毁掉。

Richardson 成熟度模型
=====================


Richardson `成熟度模型 <https://martinfowler.com/articles/richardsonMaturityModel.html>`_ ::

    RESTful Web APIs” 和 “RESTful Web Services” 的作者伦纳德・理查德森（Leonard Richardson）
    提出了一个衡量 “服务有多么 REST” 的 Richardson 成熟度模型（Richardson Maturity Model，RMM）

    Richardson 将服务接口按照 “REST 的程度”，从低到高分为 0 至 3 共 4 级：
    1. The Swamp of Plain Old XML：完全不 REST。
    2. Resources：开始引入资源的概念。
    3. HTTP Verbs：引入统一接口，映射到 HTTP 协议的方法上。
    4. Hypermedia Controls：在咱们课程里面的说法是 “超文本驱动”，
        在 Fielding 论文里的说法是 Hypertext as the Engine of Application State（HATEOAS）

第 0 级成熟度：The Swamp of Plain Old XML::

    医院开放了一个 /appointmentService 的 Web API，传入日期、医生姓名作为参数，就可以得到该时间段、该医生的空闲时间。

    1. 请求医生的空闲时间:
    POST /appointmentService?action=query HTTP/1.1
    {date: "2020-03-04", doctor: "mjones"}

    返回:
    HTTP/1.1 200 OK
    [ 
      {start:"14:00", end: "14:50", doctor: "mjones"}, 
      {start:"16:00", end: "16:50", doctor: "mjones"}
    ]

    2. 预约确认，并提交了我的基本信息:
    POST /appointmentService?action=comfirm HTTP/1.1

    {
        appointment: {date: "2020-03-04", start:"14:00", doctor: "mjones"},
        patient: {name: xx, age: 30, ……}
    }

    返回:
    a. 预约成功
    HTTP/1.1 200 OK

    {
        code: 0,
        message: "Successful confirmation of appointment"
    }

    b. 预约失败，有人在我前面抢先预约了
    HTTP/1.1 200 OK

    {
        code: 1
        message: "doctor not available"
    }

    结论: 非常直观的基于 RPC 风格的服务设计

第 1 级成熟度：Resources::

    通往 REST 的第一步是引入资源的概念
      在 API 中最基本的体现，它是围绕着资源而不是过程来设计服务

    每次请求中都应包含资源 ID，所有操作均通过资源 ID 来进行

    1. 请求医生的空闲时间:
    POST /doctors/mjones HTTP/1.1

    {date: "2020-03-04"}

    返回:
    服务器传回一个包含了 ID 的信息。
    注意，ID 是资源的唯一编号，有 ID 即代表 “医生的档期” 被视为一种资源:
    HTTP/1.1 200 OK

    [
        {id: 1234, start:"14:00", end: "14:50", doctor: "mjones"},
        {id: 5678, start:"16:00", end: "16:50", doctor: "mjones"}
    ]

    2. 预约确认，并提交了我的基本信息:
    POST /schedules/1234 HTTP/1.1

    {name: xx, age: 30, ……}

第 2 级成熟度：HTTP Verbs::

    引入统一接口（Uniform Interface）
    HTTP 协议的标准方法是经过精心设计的，它几乎涵盖了资源可能遇到的所有操作场景:

    1. 把不同业务需求抽象为对资源的增加、修改、删除等操作来解决；
    2. 针对响应代码，使用 HTTP 协议的 Status Code，可以涵盖大多数资源操作可能出现的异常（也可自定义扩展的）；
    3. 针对安全性，依靠 HTTP Header 中携带的额外认证、授权信息来解决

    1. 在获取医生档期时，应该使用具有查询语义的 GET 操作来完成
    GET /doctors/mjones/schedule?date=2020-03-04&status=open HTTP/1.1

    返回:
    HTTP/1.1 200 OK

    [
        {id: 1234, start:"14:00", end: "14:50", doctor: "mjones"},
        {id: 5678, start:"16:00", end: "16:50", doctor: "mjones"}
    ]

    2. 预约确认，并提交了我的基本信息:
    POST /schedules/1234 HTTP/1.1

    {name: xx, age: 30, ……}

    返回:
    a. 预约成功
      HTTP/1.1 201 Created

      Successful confirmation of appointment
    b. 失败
      HTTP/1.1 409 Conflict

      doctor not available

第 3 级成熟度：Hypermedia Controls::

    关键词: HATEOAS, 超文本驱动

    希望能达到这样一种效果:
      除了第一个请求是由你在浏览器地址栏输入的信息所驱动的之外，
      其他的请求都应该能够自己描述清楚后续可能发生的状态转移，由超文本自身来驱动。


    1. 在获取医生档期时，应该使用具有查询语义的 GET 操作来完成
    GET /doctors/mjones/schedule?date=2020-03-04&status=open HTTP/1.1

    返回(服务器传回的响应信息应该包括如何预约档期、如何了解医生信息等可能的后续操作):
    HTTP/1.1 200 OK

    {
        schedules：[
            {
                id: 1234, start:"14:00", end: "14:50", doctor: "mjones",
                links: [
                    {rel: "comfirm schedule", href: "/schedules/1234"}
                ]
            },
            {
                id: 5678, start:"16:00", end: "16:50", doctor: "mjones",
                links: [
                    {rel: "comfirm schedule", href: "/schedules/5678"}
                ]
            }
        ],
        links: [
           {rel: "doctor info", href: "/doctors/mjones/info"}
        ]
    }

    做到了第 3 级 REST，那么服务端的 API 和客户端就可以做到完全解耦了。
    这样一来，你再想要调整服务数量，或者同一个服务做 API 升级，将会变得非常简单。
    gordon评: 做成web页面了


REST 的不足与争议
=================

第一个有争议的问题是：面向资源的编程思想只适合做 CRUD，只有面向过程、面向对象编程才能处理真正复杂的业务逻辑::

    Google 推荐的 REST API 风格来拓展 HTTP 标准方法:
    自定义方法: https://cloud.google.com/apis/design/custom_methods

    自定义方法应该放在资源路径末尾，嵌入冒号加自定义动词的后缀,如(这儿的undelete):
    POST /user/user_id/cart/book_id:undelete

第二个有争议的问题是：REST 与 HTTP 完全绑定，不适用于要求高性能传输的场景中::

    面向资源编程与协议无关

第五个有争议的问题是：REST 缺乏对资源进行 “部分” 和 “批量” 的处理能力::

    可能是未来面向资源的思想和 API 设计风格的发展方向。

    HTTP 协议对 REST 的束缚:
    1. 缺少对资源的 “部分” 操作的支持
      例: 只是想获得某个用户的姓名
        RPC 风格中可以设计一个 “getUsernameById” 的服务
        REST 风格需向服务端请求整个用户对象，然后丢弃掉返回结果中的其他属性，这就是一种请求冗余（Overfetching）。
    2. 缺少对资源的 “批量” 操作的支持
      例: 给 1000 个用户的昵称加 “VIP” 前缀时
      例2: 在网店买东西的时候，下单、冻结库存、支付、加积分、扣减库存这一系列步骤会涉及多个资源的变化
          这时候我们就得创建一种 “事务” 的抽象资源，或者用某种具体的资源（比如 “结算单”）
          贯穿网购这个过程的始终，每次操作其他资源时都带着事务或者结算单的 ID
          对于 HTTP 协议来说，由于它的无状态性，相对来说不适用于（并非不能够）处理这类业务场景






