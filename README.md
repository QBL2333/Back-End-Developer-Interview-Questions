后端开发面试题
================

## 说明

这篇文章翻译自一位外国友人的关于面试后端程序员的文章，我比较喜爱这篇文章。一是因为它极大的拓宽了我的视角，另一方面是其中的一些问题非常具有启发性。不仅对于面试者，对于面试官来说也是个不错的参考。于是迫不及待的翻译了一下，给各位看官做个参考。

这篇文章中，许多问题我并没有完全理解，所以翻译可能存在不准确的地方。如果有读者发现有一些翻译有误或者不好的地方，请不吝赐教。

原文参见 [@arialdomartini](https://github.com/arialdomartini)的: [Back-End Developer Interview Questions](https://github.com/arialdomartini/Back-End-Developer-Interview-Questions)

以下是原文翻译。

后端开发面试题
================

在面试的时候，我并不特别喜欢问一些技术性的问题。我更喜欢的方式是这样的: 和面试者坐在一起，看一些实际的代码，解决一些实际的问题。并且用一整天的时间，让团队所有成员轮流和面试者进行结对编程。虽然如此，但是一些技术问题仍然可以用来很好地启动一段有深度的谈话，能够让面试者和面试官相互都有更加深入的了解。

这个仓库包含了可以用来考核面试者的一系列后端面试题。但绝不是说，面试官必须用每个面试题来考核面试者（这样可能要耗费好几个小时）。根据你期望面试者拥有的技能，从这个列表中有选择的挑一些题目，可以帮助你在特定技能上考核面试者。

应当承认的是，这个项目的灵感来自于[@darcyclarke](https://github.com/darcyclarke)的文章[Front-end Job Interview Questions](https://github.com/darcyclarke/Front-end-Developer-Interview-Questions)

**注意:** 请记住，这些面试题中有许多问题是开放式的，能引导讨论一些有趣的问题。相比那些有直接答案的问题来说，这种问题能够让你对面试者的能力有更多的了解。再一次强调，我认为仅仅是问问题是不够的。要通过与面试者较长时间的结对编程来完成面试: 这是你们相互了解对方的风格和方法、让面试者了解未来工作的最佳手段之一。

## <a name='toc'>目录</a>

  1. [通用问题](#general)
  1. [开放式问题](#open)
  1. [设计模式相关问题](#patterns)
  1. [代码设计相关问题](#design)
  1. [语言相关问题](#languages)
  1. [Web相关问题](#web)
  1. [数据库相关问题](#databases)
  1. [非关系型数据库相关问题](#nosql)
  1. [代码版本管理相关问题](#codeversioning)
  1. [并发问题](#concurrency)
  1. [分布式系统相关问题](#distributed)
  1. [软件生命周期和团队管理相关问题](#management)
  1. [逻辑和算法相关问题](#algorithms)
  1. [软件架构相关问题](#architecture)
  1. [面向服务架构(SOA)和微服务(Microservice)相关问题](#soa)
  1. [安全相关问题](#security)
  1. [比尔盖茨式问题](#billgates)
  1. [代码示例问题](#snippets)

#### <a name='general'>通用问题:</a> [[↑]](#toc)

* 语言设计中空引用([null reference](http://programmers.stackexchange.com/questions/12777/are-null-references-really-a-bad-thing))的存在有什么问题？假设你想要将空引用的概念从你的首选语言中移除，可能导致什么结果？
* 为什么函数式编程重要？什么时候适用函数式语言？

  可以避免this指向所带来的困扰/代码简洁，快速开发/方便的代码管理，方便调试/易于"并发编程",因为它不修改变量，所以根本不存在"锁"线程的问题/打包过程中可以过滤无用代码/关注以及使用度高，很多大型框架也在使用函数式编程

  函数式编程强调函数的纯粹性和不可变性。当项目需要处理大量并发和分布式计算时。当项目需要构建可靠和安全的系统时。当项目需要进行大规模的数据处理和分析时。

* 设计(design)、架构(architecture)、功能(functionality)和美学(aesthetic)之间有什么区别？讨论一下。
* 微软、谷歌、欧朋(opera)和火狐这类公司是如何从他们的浏览器中获利的？

  与搜索引擎合作/广告/定制服务/平台和应用集成/收集分析数据
  
* 为什么打开TCP套接字有很大的开销？

  -三次握手四次挥手 SYN SYN+ACK ACK / FIN ACK FIN ACK

* 封装的重要性体现在哪儿？

  将复杂的问题分解为一系列独立、可重用的逻辑单元,极大地增强了代码的可读性、可维护性和扩展性

* 什么是实时系统？它与普通系统有什么区别？

  响应存在时间限制，并发请求依据优先级处理

* 实时语言(real-time language)和堆内存分配(heap memory allocation)之间的关系是什么？
* 不变性(Immutability)是指: (变量的)值只能在创建的时候被设置一次，之后就不能被改变。为什么不变性对写更加安全的代码有帮助？
* 可变值(mutable values)和不可变值(immutable values)有哪些优缺点？
* 什么是O/R阻抗失衡(Object-Relational impedence mismatch)？

  实际的对象类型数据与关系型数据库的实现无法达到完全一致（如ID列）

* 如果你需要使用缓存，你使用哪些原则来确定缓存的大小？

  总数据15-30%
  
* TCP和HTTP有什么区别？

  TCP传输层 HTTP应用层 HTTP是建立在TCP可靠连接上的应用层协议

* 在客户端渲染(client-side rendering)和服务端渲染(server-side rendering)之间，你是如何权衡的？
* 如何在一个不可靠的协议之上构建一个可靠的通信协议？

  手动添加TCP的机制，如超时重传，有序接收，应答确认

#### <a name='open'>开放式问题:</a> [[↑]](#toc)

* 为什么人们会抵制变化？
* 如何向你的祖母解释什么是线程？
* 作为一个软件工程师，你想要既要有创新力，又要产出具有可预测性。采用什么策略才能使这两个目标可以共存呢？
* 什么是好的代码？
* 解释什么是流(Streaming)和如何实现一个流？

  支持读写和查找的Stream类型

* 假设你的公司给你一周的时间，用来改善你和同事的生活: 你将如何使用这一周？
* 本周你学了什么？
* 所有的设计中都会有美学元素(aesthetic element)的存在。问题是，你认为美学元素是你的朋友还是敌人？
* 列出最近你读过的5本书。
* 假设目前有个大型公司（非常有钱），他们的开发流程是瀑布式流程（Waterfall），如果需要你在他们公司引入持续交付（[Continue Devivery](https://en.wikipedia.org/wiki/Continuous_delivery)），你会怎么做？

  瀑布是线性流程，引入迭代，在每个迭代进行一个完整的瀑布
  
* 我们来谈谈"*重复造轮子*","*非我发明症*", "*吃自己做出来的狗粮*"的这些做法吧。

(注: 重复造轮子: Reinventing the wheel; 非我发明症:Not Invented Here Syndrome; 吃自己做出来的狗粮: Eating Your Own Dog Food)

* 在你当前的工作流中，什么事情是你计划下一步需要自动化的？
* 为什么写软件是困难的？是什么使软件的维护变得困难？
* 你更喜欢在全新项目（Green Field Project）上工作还是在已有项目(Brown Field Project)基础上工作？为什么？
* [当你在浏览器地址栏输入google.com回车之后都发生了什么?](https://github.com/alex/what-happens-when)
* 当操作系统CPU处于空闲的时候，它可能在处理哪些事情？
* 如何向一个5岁的孩子解释什么是Unicode（统一码）/数据库事务？
* 如何维护单体架构(monolithic architecture)？

  与微服务架构相对，所有功能在一个repo

* 一个"专业的开发者"意味着什么？
* 软件开发是艺术、是技艺还是工程？你的观点是什么？
* "喜欢这个的人也喜欢..."，如何在一个电子商务商店里实现这种功能？

  大数据智能推荐-协同过滤

* 为什么在创新上，企业会比创业公司慢些？
* 为什么说，对于涉及密码学的问题，你不应该尝试应用自己的发明或者设计？

#### <a name='patterns'>设计模式相关问题:</a> [[↑]](#toc)

* 请用一个例子表明，全局对象是邪恶的存在。
* 假设你工作的系统不支持事务性，你会如何从头开始实现它？

  原子性 隔离性 一致性 持久性 队列维护操作请求

* 什么是好莱坞原则（Hollywood Principles）？

  底层组件提供服务，而非顶层去依赖底层——关注抽象的接口而非实现本身

* 关于迪米特法则(最少知识原则): 写一段代码违反它, 然后修复它。 

（注: 迪米特法则：the Law of Demeter, 最少知识原则： the Principle of Least Knowledge）

  类之间尽量不要相互引用
* Active-Record模式有什么限制和缺陷？

  类对应表，表的一条对应一个实例

* Data-Mapper模式和Active-Record模式有什么区别？

  DM类的结构与表存储方式无关，AR要求类和表一致
  
* 空对象模式(Null Object Pattern)的目的是什么？

  避免调用null的接口时导致Exception
  
* 为什么组合(Composition)比继承(Inheritance)更好？

  继承关系复杂时代码可读性可维护性差
  
* 什么是反腐败层(Anti-corruption Layer)?

  将设计不好的旧系统的接口转化为可读性好的新接口，避免业务代码受旧系统影响
  
* 你可以写一个线程安全的单例(Singleton)类吗？

  INSTANCE 线程安全：定义时即初始化/访问时初始化但加锁
  
* 数据抽象(Data Abstraction)能力是指能改变实现而不影响客户端的这种能力。请构造一个一个例子，违反这个特性，并且尝试修复它。
* 你是如何处理依赖关系地狱(Dependency Hell)的？

  依赖分身，对于不同模块使用同一个依赖时使用不同版本

* 为什么说goto语句是恶魔般的存在？
* 健壮性是进行软件设计时的一个通用原则，它建议 *“发送时要保守，接收时要开放”*。这也经常被写成，“做一个有耐心的读者，做一个谨慎的作者”。你能解释一些这背后的逻辑吗？

译者注： "发送时要保守，接收时要开发"的原文是： "Be conservative in what you send, be liberal in what you accept"，有点类似于“严于律己，宽于待人”的意味。

#### <a name='design'>代码设计相关问题:</a> [[↑]](#toc)

* 你在进行软件设计时会考虑软件测试吗？软件测试是如何影响软件设计的？
* 内聚和耦合的区别是什么？

  模块内部和模块外部，高内聚低耦合
  
* 重构在哪些场景下有用？
* 代码中的注释有用吗？
* 设计和架构有什么区别？
* 为什么在测试驱动开发(TDD)中是先写测试，再写代码？

  为了尽快实现功能
  
* C++支持多继承，Java 允许类实现多个接口。这些特性对正交性有什么影响？使用多继承和使用多接口有区别吗？[这个问题来自Andrew .Hunt 和 David Thomas写的《程序员修炼之道》]

  正交性：改变一个不影响另一个。多继承影响正交，多接口对正交无影响。
  
* 在存储过程（Stored Procedures）中写业务逻辑有什么优缺点？

  优点：易于开发，逻辑简单时容易维护 缺点：高并发时压力大，不容易扩展
  

#### <a name='languages'>语言相关问题:</a> [[↑]](#toc)

* 告诉我你的首选语言的三个最坏的缺陷。

  运行慢 代码不简洁 性能较低
  
* 为什么现在函数式编程这么越来越受关注？
* 闭包是什么？它有什么用途？闭包和类有什么共同点？

  访问另一个函数内部变量的函数 都用于封装和抽象
    
* 泛型有什么用途？

  传参类型T
  
* 什么是高阶函数？有什么用途？用你的首选语言写个例子出来。

  函数作为参数/返回值
  
* 讨论一下，如何写一个循环，然后把它转换成递归函数，要避免易变性。

  易变性：原子操作依赖于之前的值，不使用同步操作可能导致读到预期之外的值
  
* 有些语言将函数视为第一公民，这是什么意思？

  函数除了可以被调用还可以像变量一样使用
  
* 用一个例子说明匿名函数是有用的。

  lambda表达式
  
* 什么是动态方法调度(Dynamic Method Dispatch)？

  多态
  
* 名字空间(Namespace)有什么用？有什么可以替代它的吗？

  package/import 避免命名冲突 
  
* 谈谈Java和C#之间的互操作性(Interoperability) (任选其他两门语言都行)

  通过工具打包让对面可识别并调用
  
* 为什么很多软件工程师不喜欢Java？
* 你认为好的语言好在哪里？差的语言差在哪里？
* 写两个函数，一个是"引用透明的(Referentially Transparent)"，另一个是"引用不透明的(Referentially Opaque)"。讨论之。

  表达式和值的互换在任何情况下都不会导致不同结果就是透明
  
* 什么是栈？什么是堆？
* 为什么一个语言中，"函数是第一公民"是很重要的？
* 模式匹配(Pattern Matching)和Switch语句(Switch clauses)的区别在哪儿？

  instanceof

* 为什么有些语言设计上没有异常机制？这有什么优缺点？

  代码简洁 debug时不容易直观看到问题原因

* 如果`Cat`是一个`Animal`, 那么`TaskCare<Cat>`是一个`TakeCare<Animal>`吗？

  泛型 是
  

#### <a name='web'>web相关问题:</a> [[↑]](#toc)

* 为什么"第一方cookie(first-party cookie)"和"第三方cookie(third-party cookie)"被如此不同的对待？

  第三方是跨网站保存用户的数据，可能涉及用户浏览习惯的隐私
  

#### <a name='databases'>数据库相关问题:</a> [[↑]](#toc)

* 如果要你将一个项目从MySQL迁移至PostgreSQL中，你会如何迁移？

  迁移数据和表，更改DAO语法，更新索引和约束
  
* 为什么```SELECT * FROM table WHERE field = null```不能匹配空的字段？

  =是equals，表示存储了值null而不是值为空

* 什么是ACID(原子性，一致性，隔离性，持久性)原则？
* 你是如何进行数据库模式(Database schema)迁移的？

  flyway or backfill？

* 延迟加载(lazy loading)是如何实现的？什么场景下有用？他有什么缺陷？

  占位 数据多数据库负载大 线程不安全/内存泄漏

* 什么是N+1问题？

  一个查询执行了N+1次，1次主表N次副表

* 如何找出应用中开销最大的查询？

#### <a name='nosql'>非关系型数据库相关问题:</a> [[↑]](#toc)

* 什么是最终一致性(Eventual Consistency)？

  在不进行后续操作的情况下保证数据一致

* 关于CAP理论，举一些CP、AP、CA系统的例子。

  C一致性A可用性P分区容错性 CA银行系统 CP数据库系统 AP社交软件

* NoSQL是如何解决可伸缩性的挑战的？

  分布式存储增加节点以扩大存储容量

* 什么情况下你会使用类似于MongoDB的文档数据库而不是关系型数据库（如Mysql或者PostgreSQL）？

  需要可扩展，大数据量，且不需要过于复杂查询


#### <a name='codeversioning'>代码版本管理相关问题:</a> [[↑]](#toc)

* 为什么在Mercurial或者git中(管理)分支比SVN容易？

  git只需要复制仓库ID，svn需要实际去复制一次分支版本文件

* 分散式版本控制系统（比如git），相比集中式版本控制系统（如svn）有哪些优势和劣势？

(注:集中式版本控制系统: Centralized Version Control Systems；分散式版本控制系统: Distributed Version Control Systems)

  优点 分布式不依赖于服务器 无需时刻联网 提交修改时不一定需要基于最新版 提交不会被打断
   
  缺点 不容易知道其他人的修改 无法实施目录级的权限控制

* 能描述一下什么是GitHubFlow和GitFlow工作流吗？

  gitflow develop+master两个分支，定期把dev合并进master githubflow 只有一个master，发布时通过request

* 什么是rebase？

  将本地commit移到master上最后，保证线性提交

* 为什么合并操作(merge)在Mercurial和git中比在SVN和CVS中容易？

  git只要没有冲突就可以直接merge，svn如果有其他人修改过同一个文件就不能直接merge必须手动修改
  

#### <a name='concurrency'>并发问题:</a> [[↑]](#toc)

* 为什么我们需要并发呢？解释一下。
* 为什么测试多线程/并发代码这么困难？
* 什么是竞争条件（Race Condition）？用任何一个语言写一个例子。

  两个线程修改同一个变量，最终的值依据较慢的线程

* 什么是死锁？用代码解释一下。

  两个线程互相等待对方释放锁

* 什么是饿死？

  低优先级的线程一直得不到执行

* 什么是Wait-Free算法？

  lock-free 不使用锁 wait-free 所有线程都能有限步骤执行完且不依赖其他线程的进展
  

#### <a name='distributed'>分布式系统相关问题:</a> [[↑]](#toc)

* 怎么测试一个分布式系统？
* 什么场景下你会在两个系统中采用异步通信机制？
* 远程过程调用的通用缺点是什么？
* 如果你为了可扩展性和鲁棒性而构建一个分布式的系统，分别在封闭安全的网络环境情况下，和地理上的位置不同但是网络环境不是封闭和安全的情况下，你会考虑什么不同的事情？
* 在Web应用中如何管理容错性？在桌面端呢？
* 在分布式系统中，如何处理故障？
* 让我们来谈谈在网络分区(network partitions)情况下的几种（一致性）解决方案吧。
* 你认为分布式计算中有哪些谬论？
* 你在什么时候会使用Request/Response模式，什么时候使用Publish/Subscribe模式？

#### <a name='management'>软件生命周期和团队管理相关问题:</a> [[↑]](#toc)

* 什么是敏捷（Agility）？
* 你是如何处理遗留代码（Legacy Code）的？
* 假设我是你们公司的CEO，请向我解释什么是看板，并且说服我在它上面投资。
* 敏捷（Agility）和瀑布（Waterfall）之间的最大区别是什么？
* 作为团队管理者，你对会议太多这个问题是如何处理的？
* 你会如何处理延期很长时间了的项目？
* "*个体与交互重于过程和工具*"和"*客户协作重于合同谈判*"占了敏捷宣言（Agile Manifesto）的一半，谈论一下这两个观念。

* 如果你是你们公司的CTO，你会采取什么样的决策？
* 你觉得项目经理有用吗？
* 如果要你组织一个弹性工作制的开发团队（即没有强制工作时间的要求），并且假期制度是"按需休假"，你会如何做？
* 你会如何管理一个人员流动非常高的团队？如何在不加薪的条件下说服团队成员不要离开？
* 除了代码之外，你最关注你的同事的哪3项素质？
* 关于代码，你最希望非技术人员能知道的的三件事是什么？

#### <a name='algorithms'>逻辑和算法相关问题:</a> [[↑]](#toc)

* 只用LIFO栈如何构造一个FIFO队列？只用FIFO队列如何构造一个LIFO栈？
* 写一段有栈溢出的代码。
* 写一个尾递归版本的阶乘函数。
* 使用任何一个语言，写一个REPL，功能是echo你输入的字符串。然后将它演化成一个逆波兰表达式的计算器。
* 如果需要你设计一个文件系统磁盘碎片整理程序，你会如何设计？
* 写一个生成随机迷宫的程序。
* 写一段有内存泄漏的示例代码。
* 随机生成一个的数字序列，里面每个数字都不同。
* 写一个简单的垃圾回收系统。
* 使用任何一门语言，写一个基本的消息代理。
* 写一个基础的web服务器，然后画一张线路图，展示你将来还想要实现的功能。
* 如何对一个10GB的文件进行排序？如果是10TB的数据，你会采用什么方法？
* 请实现`rnd()`函数

#### <a name='architecture'>软件架构相关问题:</a> [[↑]](#toc)

* 什么情况下缓存是没用的，甚至是危险的？
* 为什么事件驱动的架构能提高可扩展性(scalability)？
* 什么样的代码是可读性强的代码？
* 紧急设计(Emergent Design)和演化架构(Evolutionary Architecture)之间的区别是什么？
* 横向扩展(scale out) vs 纵向扩展(scale up): 有什么区别？分别在什么场景下使用？
* 分布式系统中如何处理"故障切换(failover)"和"用户会话(user session)"？
* 什么是CQRS(Command Query Responsibility Segregation)?他和最早的Command-Query Separation原则有什么区别？
* 什么是三层架构？
* 如何设计一个可扩展性高的系统？
* 处理C10k问题的策略有哪些？
* 如果让你来设计一个去中心化的P2P系统，你会如何设计？
* 为什么CGI的扩展性不好？
* 在设计系统时，你如何防止供应商依赖([Vendor Lock-in](https://sourcemaking.com/antipatterns/vendor-lock-in))？
* 在可扩展性上，发布/订阅(Publish-Subscribe)模式有什么缺点？
* 80年代以后，CPU有哪些变化？这些变化，对编程产生了什么影响？
* 性能生命周期(performace lifecycle)中，你认为哪个部分是需要考虑进去的？ 如何管理？
* 除了恶意攻击造成的拒绝服务现象以外，哪些设计或者架构上的问题会导致拒绝服务？
* 性能和可扩展性之间有什么关系？
* 什么时候紧耦合是OK的？
* 一个系统要有什么特征才能适配云计算环境(Cloud Ready)？
* Does unity of design imply an aristocracy of architects?

#### <a name='soa'>面向服务架构(SOA)和微服务(Microservice)相关问题:</a> [[↑]](#toc)

* 在SOA中，为什么长期存活的事务(Long-lived transation)不被看好，而Saga却被看好？
* SOA和MicroService之间有什么区别？
* 我们来谈谈Web服务的版本管理、版本兼容性、重大变更管理这些事情吧.
* 在saga中事务和补偿操作(compensation operation)之间的区别是什么？在SOA中呢？
* 微服务不能做得太"微"，你认为什么时候微服务太"微"了？
* MicroService架构的优劣是什么？

#### <a name='security'>安全相关问题:</a> [[↑]](#toc)

* 什么是双因素认证(Two Factor Authentication)？在一个已有的Web应用中，你如何实现这种机制？

#### <a name='billgates'>比尔盖茨式问题:</a> [[↑]](#toc)

* 如果你把一面镜子放在扫描仪上，会发生什么？
* 假设有一个和你完全一样的克隆人，而他是你的上司，你愿意和他工作吗？
* 现在请你面试一下我。
* 为什么Quora上的回答会比Yahoo Answer上的回答好？
* 对手是现代语言，你的任务是要为Cobol辩护，你会如何进行？
* 10年后的你是什么样子？
* 假设你是我老板，我被解雇了。你会如何通知我？
* 我想要重构一个系统，而你想要从头重写。我们来争论一下该怎么弄吧。然后我们反转角色，再争论一下。
* 老板要你对公司撒谎，你的反应是什么？
* 如果你可以穿越到以前，你会给年轻时候的你什么建议？

#### <a name='snippets'>代码示例问题:</a> [[↑]](#toc)

* 这段Javascript函数的输出是什么？

```javascript
function hookupevents() {
  for (var i = 0; i < 3; i++) {
    document.getElementById("button" + i)
      .addEventListener("click", function() { 
        alert(i); 
      });
  }
}
```

* 关于类型擦除(Type Erasure)，这段Java代码的输出是什么？为什么？

```java
ArrayList<Integer> li = new ArrayList<Integer>();
ArrayList<Float> lf = new ArrayList<Float>();
if (li.getClass() == lf.getClass()) // evaluates to true
  System.out.println("Equal");
```

* 你能指出哪儿有内存泄漏吗？

```java
public class Stack {
    private Object[] elements;
    private int size = 0;
    private static final int DEFAULT_INITIAL_CAPACITY = 16;

    public Stack() {
        elements = new Object[DEFAULT_INITIAL_CAPACITY];
    }

    public void push(Object e) {
        ensureCapacity();
        elements[size++] = e;
    }
   
    public Object pop() {
        if (size == 0)
            throw new EmptyStackException();
        return elements[--size];
    }

    /**
     * Ensure space for at least one more element, roughly
     * doubling the capacity each time the array needs to grow.
     */
    private void ensureCapacity() {
        if (elements.length == size)
            elements = Arrays.copyOf(elements, 2 * size + 1);
    }
}
```

* `if`语句，或者更加通用点，条件表达式通常是过程式编程/命令式编程的形式。你能去掉这段代码中的`switch`语句，用面向对象的方式来修改这段代码吗？

```java
public class Formatter {

    private Service service;

    public Formatter(Service service) {
        this.service = service;
    }

    public String doTheJob(String theInput) {
        String response = service.askForPermission();
        switch (response) {
        case "FAIL":
            return "error";
        case "OK":
            return String.format("%s%s", theInput, theInput);
        default:
            return null;
        }
    }
}
```

* 你能去掉这里的`if`语句，将它改成更加面向对象吗？

```java
public class TheService {
    private final FileHandler fileHandler;
    private final FooRepository fooRepository;

    public TheService(FileHandler fileHandler, FooRepository fooRepository) {
        this.fileHandler = fileHandler;
        this.fooRepository = fooRepository;
    }

    public String Execute(final String file) {

        final String rewrittenUrl = fileHandler.getXmlFileFromFileName(file);
        final String executionId = fileHandler.getExecutionIdFromFileName(file);

        if ((executionId == "") || (rewrittenUrl == "")) {
            return "";
        }

        Foo knownFoo = fooRepository.getFooByXmlFileName(rewrittenUrl);

        if (knownFoo == null) {
            return "";
        }

        return knownFoo.DoThat(file);
    }
}
```

* 如何重构这段代码？

```javascript
function()
{
    HRESULT error = S_OK;

    if(SUCCEEDED(Operation1()))
    {
        if(SUCCEEDED(Operation2()))
        {
            if(SUCCEEDED(Operation3()))
            {
                if(SUCCEEDED(Operation4()))
                {
                }
                else
                {
                    error = OPERATION4FAILED;
                }
            }
            else
            {
                error = OPERATION3FAILED;
            }
        }
        else
        {
            error = OPERATION2FAILED;
        }
    }
    else
    {
        error = OPERATION1FAILED;
    }

    return error;
}
```

