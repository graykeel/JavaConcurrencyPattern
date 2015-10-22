Java Concurrency Pattern
======================

《Java多线程编程模式实战指南》系列文章配套源码。这些文章已扩充为一本书：《Java多线程编程实战指南（设计模式篇）》，由电子工业出版社出版，当当、亚马逊、京东、互动出版网、淘宝等各大书店有售。

【样章】

Active Object模式：

http://www.infoq.com/cn/articles/Java-multithreaded-programming-mode-active-object-part1

http://www.infoq.com/cn/articles/Java-multithreaded-programming-mode-active-object-part2

Immutable Object模式：

http://www.infoq.com/cn/articles/java-multithreaded-programming-mode-immutable-object

Two-phase Termination模式：

http://www.infoq.com/cn/articles/java-multithreaded-programming-mode-two-phase-termination

http://viscent.iteye.com/category/328291

【前言】

随着现代CPU的生产工艺从提升CPU主频频率转向多核化，即在一块芯片上集成多个CPU内核（Core），以往那种靠CPU自身处理能力的提升所带来的软件计算性能提升的那种“免费午餐”不复存在。在此背景下，多线程编程在充分利用计算资源、提高软件服务质量方面扮演了越来越重要的角色。然而，多线程编程并非一个简单地使用多个线程进行编程的数量问题，其又有自身的问题。好比俗话说“一个和尚打水喝，两个和尚挑水喝，三个和尚没水喝”，简单地使用多个线程进行编程可能导致更加糟糕的计算效率。
设计模式相当于软件开发领域的“三十六计”，它为特定背景下反复出现的问题提供了一般性解决方案。多线程相关的设计模式为我们恰当地使用多线程进行编程并达到提升软件服务质量这一目的提供了指引和参考。当然，设计模式不是菜谱，即便是菜谱我们也不能指望照着菜谱做就能做出一道美味可口的菜肴，但我们又不能因此而否认菜谱存在的价值。
可惜的是，国外与多线程编程相关的设计模式书籍多数采用C++作为描述语言，且书中所举的例子又多与应用开发人员的实际工作经历相去甚远。本书作为国内第一本多线程编程相关设计模式的原创书籍，希望能够为Java开发者普及多线程相关的设计模式开一个头。
本书采用Java（JDK 1.6） 语言和UML（Unified Modeling Language）为描述语言，并结合作者多年工作经历的相关实战案例，介绍了多线程环境下常用设计模式的来龙去脉：各个设计模式是什么样的及其典型的实际应用场景、实际应用时需要注意的相关事项以及各个模式的可复用代码实现。
本书第1章对多线程编程基础进行了回顾，虽然该章讲的是基础但重点仍然是强调“实战”。所谓“温故而知新”，有一定多线程编程基础、经验的读者也不妨快速阅读一下本章，说不定有新的收获。
本书第3章到第14章逐一详细讲解了多线程编程相关的12个常用设计模式。针对每个设计模式，相应章节会从以下几个方面进行详细讲解。
模式简介。这部分简要介绍了相应设计模式的由来及其核心思想，以便读者能够快速地对其有个初步认识。
模式的架构。这部分会从静态（类及类与类之间的结构关系）和动态（类与类之间的交互）两个角度对相应设计模式进行详细讲解。模式架构分别使用UML类图（Class Diagram）和序列图（Sequence Diagram）对模式的静态和动态两个方面进行描述。
实战案例解析。在相应设计模式架构的基础上，本部分会给出相关的实战案例并对其进行解析。不同于教科书式的范例，实战案例强调的是“实战”这一背景。因此实战案例解析中，我们会先提出实际案例中我们面临的实际问题，并在此基础上结合相应设计模式讲解相应设计模式是如何解决这些问题的。实战案例解析中我们会给出相关的Java代码，并讲解这些代码与相应设计模式的架构间的对应关系，以便读者进一步理解相应设计模式。为了便于读者进行实验，本书给出的实战案例代码都力求做到可运行。实战案例解析有助于读者进一步理解相应的设计模式，并体验相应设计模式的应用场景。建议读者在阅读这部分时先关注重点，即实战案例中我们要解决哪些问题，相应设计模式又是如何解决这些问题的，实战案例的代码与相应设计模式的架构间的对应关系。而代码中其与设计模式非强相关的细节则可以稍后关注。
模式的评价与实现考量。这部分会对相应设计模式在实现和应用过程中需要注意的一些事项、问题进行讲解，并讨论应用相应设计模式所带来的好处及缺点。该节也会讨论相应设计模式的典型应用场景。
可复用实现代码。这部分给出相应设计模式的可复用实现代码。编写设计模式的可复用代码有助于读者进一步理解相应设计模式及其在实现和应用过程中需要注意的相关事项和问题，也便于读者在实际工作中应用相应设计模式。
Java标准库实例。考虑到Java标准库的API设计过程中已经应用了许多设计模式，本书尽可能地给出相应设计模式在Java API中的应用情况。
相关模式。设计模式不是孤立存在的，一个具体的设计模式往往和其它设计模式之间存在某些联系。这部分会描述相应设计模式与其它设计模式之间存在的关系。这当中可能涉及GOF的设计模式，这类设计模式并不在本书的讨论范围之内。有需要的读者，请自行参考相关书籍。
本书的源码可以从http://github.com/Viscent/javamtp下载或博文视点官网http://www.broadview.com.cn相关图书页面。

【本书目录】见：http://www.phei.com.cn/module/goods/wssd_content.jsp?bookid=43821
