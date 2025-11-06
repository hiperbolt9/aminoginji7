# EventOS Nano产品说明

<a href='https://gitee.com/event-os/eventos-nano/stargazers'><img src='https://gitee.com/event-os/eventos-nano/badge/star.svg?theme=dark' alt='star'></img></a><a href='https://gitee.com/event-os/eventos-nano/members'><img src='https://gitee.com/event-os/eventos-nano/badge/fork.svg?theme=dark' alt='fork'></img></a>

邮箱：**event-os@outlook.com**，微信号：**Event-OS**，QQ群：**667432915**。

-------
### 一、EventOS Nano是什么？
**EventOS Nano**，是一个面向单片机、事件驱动的嵌入式开发平台。它主要有两大技术特色：一是事件驱动，二是超轻量。**EventOS Nano**以及其母项目**EventOS**，目标是开发一个企业级的嵌入式开发平台，以**事件总线**为核心，打造一个统一的嵌入式技术生态，为广大企业用户和嵌入式开发者们，提供搞可靠性的、高性能的、现代且高开发效率的嵌入式开发环境。

**EventOS Nano**的主要特性列举如下：
+ **事件总线**为核心组件，灵活易用，是进行线程（状态机）间同步或者通信的主要手段，也是对EventOS分布式特性和跨平台开发进行支持的唯一手段。事件支持**广播**发送，或者**发布-订阅**机制两种方式（二选一）。
+ **全局事件队列**，摒弃每个线程（状态机）拥有自己的事件队列的方式，只有一个全局事件队列，极限压缩对RAM的占用。
+ **协作式内核**，优点是不会产生资源竞争，极度可靠。
+ **极度轻量，便于嵌入其他系统**，除事件总线外的所有特性（层次状态机、平面状态机、发布-订阅机制、事件携带数据、事件桥等）均可裁剪，将资源占用降至极限，可**低至ROM 1.2KB，RAM 172Byte**。可以作为子系统，“悄悄”嵌入到其他软件系统中去。
+ **功能强大的软定时器**，以时间事件的形式，对软定时器功能，进行优雅且功能强大的实现。
+ API的设计，更加简明，更加符合本土嵌入式工程师的习惯。
+ 移植方便，只需实现少数几个接口函数即可。
+ 未来会使用**Event Bridge**（事件桥）机制与**EventOS**打通事件总线，以便对**EventOS**的分布式特性进行支持。
+ 重点关注三种应用场景：中小资源单片机，作为模块向其他软件系统的嵌入和可靠性要求较高的嵌入式场景。

**EventOS Nano**的前身，曾经让我在过去的工作中受益匪浅，让我非常高效的写出了很多可靠的程序，能力和回报都有了质的提升。现在，我将以前的技术成果整理重构，在各方面都向着规范的开源项目靠拢，包括源码、注释、文档、单元测试和例程等等。未来，**EventOS Nano**这个项目我会一直完善下去。我的目标是，将**EventOS Nano**项目在2022年底前做成Gitee推荐项目，2024年年底前将**EventOS**项目，做成Gitee的GVP项目。造福更多的嵌入式工程师。

### 二、文档与博客
**EventOS Nano**的移植和入门，在**documentation**文件夹里，可以参考以下几个文档：
+ [快速入门文档](/documentation/UM-02-001-QuickStart.md)
+ [裸机移植文档](/documentation/UM-02-002-PortMetal.md)
+ [开发环境搭建](/documentation/UM-02-003-DevEnv.md)

**EventOS Nano**有关的博客：
+ [如何理解事件](/blog/如何理解事件.md)

### 三、为什么叫做EventOS Nano？
之所以叫**Nano**，是因为它真的非常轻量。全功能的**EventOS Nano**目前经MDK编译后，框架本身占用RAM 200Byte，ROM约3.5KB（优化等级为-O3）或4.5KB（优化等级为-O0）。裁剪后，最小功能的**EventOS Nano**，目前经MDK编译后，框架本身占用RAM 172Byte，ROM约1.2KB（优化等级为-O3）或1.5KB（优化等级为-O0）。

之所以叫**EventOS Nano**，一是因为它的技术特色与核心思想，就是**事件驱动**；二是因为它是另外一个开源项目**EventOS**（准备中）的简化实现，**EventOS**是一个**事件驱动**的、**分布式**的、**可跨平台开发**的嵌入式RTOS，面向32位单片机和更高处理器的嵌入式开发平台。

### 四、EventOS Nano主张的编程思想
#### **事件驱动**与**事件总线**
事件驱动和事件总线，是**EventOS Nano**的核心，也是**EventOS**的核心。事件机制，与RTOS中事件概念完全不同，它更像是windows编程中的消息。事件，可以认为是**主题 + 不定长数据**，通过事件，可以极大解耦模块间的耦合，增强软件的可测试性，还可以进行跨平台开发和分布式扩展。

#### **防御式编程**
**EventOS Nano**使用了大量的断言，对系统的运行过程和用户对**EventOS Nano**的使用进行大量的检查。我们强烈建议，用户要对断言接口函数进行精心的设计和实现，在实际的产品代码中，依然打开断言。这样，软件将以非常快的速度，收敛于稳定状态。

#### **跨平台开发**
**EventOS Nano**提倡跨平台开发。所谓跨平台开发，就是在Windows和Linux等便捷友好的开发环境里，完成绝大部分的开发工作，包括编程、调试、运行和单元测试等工作，然后在目标平台上进行最后的移植、调试和适配工作。跨平台的优点有很多，比如开发效率非常高、工程师进入到更多的编程领域和程序稳定可靠等。**EventOS Nano**主要在32位MinGW平台和Linux平台上开发。开发环境的搭建，见文档[开发环境搭建](/documentation/UM-02-003-DevEnv.md)。当然，也完全可以用MDK在单片机上直接开发，效率稍低而已。

#### **消除耦合**

无论是广播式的事件发送机制，还是发布-订阅式的事件发送机制，实际上，都是为了消除软件模块间的耦合。

### 五、EventOS Nano项目的维护原则
#### 但行好事，不问前程

我完全没有考虑过**EventOS Nano**将来能够如何，而且最近**EventOS Nano**的发展有点超出我预计，我有点受宠若惊。更多的人了解**EventOS Nano**是一件好事，敦促这我把**EventOS Nano**项目尽快做好，做完善，做成一个工业级的软件产品，为广大的嵌入式工作者创造便利。希望**EventOS Nano**最终被众多工程师和企业认可，并在成千上万的嵌入式产品中广泛应用起来，那就不枉我这些年深挖技术的努力。

#### 源码文档并进
我深知完善丰富的文档，对一个开源项目的重要意义。因此，我坚持每一个特性的升级，每一个BUG的修复，都跟随着相应的文档。让**EventOS Nano**和**EventOS**项目的文档专业化、体系化，包含用户手册、版本特性、原理说明、博客、例程等等。

#### 单元测试优先
嵌入式的开源项目，用户最关心的，是软件的可靠性。单元测试，是保证软件健壮与可靠的重要手段。对于**EventOS Nano**这种系统级、框架级的软件，稳定性与可靠性更加重要。从**EventOS Nano**诞生之日起，它就是面向单元测试的。详尽而严谨的单元测试，保证了**EventOS Nano**将绝大多数的BUG，消除在了开发阶段。**EventOS Nano**的每一次重构、升级与发布，都是经过了严谨的单元测试的。

#### 用户至上，需求至上
软件如何发展，代码向哪个方向前进，**EventOS Nano**完全听从用户们的声音，完全从需求出发。我们从各个渠道，微信、QQ、论坛等获取的意见建议，都将体现到**EventOS Nano**的开发中去。

### 六、代码结构
#### **核心代码**
+ **eventos/eventos.c** EventOS Nano状态机框架的实现
+ **eventos/eventos.h** 头文件
+ **eventos/eventos_config.h** 对EventOS Nano进行配置与裁剪

#### **第三方代码库**
+ **RTT** Segger JLink所提供的日志库，依赖于JLink硬件。
+ **unity** 单元测试框架

#### **例程代码**
+ **freertos** 对FreeRTOS的适配例程（未完成）。
+ **posix** 对符合POSIX标准的操作系统（如Linux、VxWork、MinGW等)的适配例程。
+ **stm32f030** 对ARM Cortex-M0芯片的裸机运行（无RTOS）的例程。
+ **stm32f103** 对ARM Cortex-M3芯片的裸机运行（无RTOS）的例程。
+ **test** 对源码进行的单元测试例程。
+ **digital_watch** 电子表例程，状态机的典型应用。
#### **tools**
一些Python脚本和工具。

#### **文档**
文档包含Doxygen代码文档的生成路径（未完成）、图片、代码相关文档（如快速入门文档、移植文档、开发环境搭建说明文档等）。
