# EventOS Nano源码说明
-------
### 概述
本代码命名为EventOS Nano。

EventOS Nano，是开源的嵌入式开发平台EventOS（整理中）在小资源单片机（Cortex-M0/16/8位单片机）的精简版本。由于其足够轻量，也可以作为子系统，悄悄嵌入到其他软件系统中去。

总体而言，EventOS Nano的基本思想，脱胎于QP状态机框架（www.state-machine.com）。但与QP框架相比，EventOS Nano项目做了很多理念上和实现上的调整。这些调整包含但不限于：
+ 事件总线为核心组件，灵活易用，是进行线程（状态机）间同步或者通信的主要手段，也是对EventOS分布式特性和跨平台开发进行支持的唯一手段。
+ 极度轻量，除事件总线外的所有特性（层次状态机、平面状态机、发布-订阅机制、事件携带数据、事件桥等）均可裁剪，将资源占用降至极限。
+ 仅支持软实时，不再关注硬实时特性（QP对硬实时的支持，导致其使用上颇有不便之处）。
+ API的设计，更加符合本土嵌入式工程师的习惯。
+ 更加便于移植，只需实现少数几个接口函数即可。
+ 暂时不考虑支持QM工具（如果网友强烈要求，可以再讨论）。
+ 未来会使用Event Bridge机制与EventOS打通事件总线，以便对EventOS的分布式特性进行支持。
+ 重点关注三种应用场景：小资源单片机，作为模块向其他软件系统的嵌入和可靠性要求较高的嵌入式场景。

### 代码结构
+ **核心代码**
    + **eventos/eventos.c** EventOS Nano状态机框架的实现
    + **eventos/eventos.h** 头文件
    + **eventos/eventos_config.h** 对EventOS Nano进行配置与裁剪
+ **第三方代码库**
    + **RTT** Segger JLink所提供的日志库，依赖于JLink硬件。
    + **unity** 单元测试框架
+ **例程代码**
    + **freertos** 对FreeRTOS的适配例程（未完成）。
    + **posix** 对符合POSIX标准的操作系统（如Linux、VxWork、MinGW等)的适配例程（未完成）。
    + **arm-cm0** 对ARM Cortex-M0芯片的裸机运行（无RTOS）的例程（未完成）。
    + **arm-cm3** 对ARM Cortex-M3芯片的裸机运行（无RTOS）的例程（未完成）。
    + **test** 对源码进行的单元测试例程。
    + **digital_watch** 电子表例程，状态机的典型应用。
+ **应用代码**
一些公共的应用层模块的实现，如LED的闪烁等。
+ **文档**
文档包含Doxygen代码文档的生成路径（未完成）、图片、代码相关文档（如快速入门文档、移植文档、开发环境搭建说明文档等）。

### 未来的开发路线
EventOS Nano曾经让我在过去的工作中受益匪浅，让我非常高效的写出了很多可靠的程序，能力和回报都有了质的提升。未来，EventOS Nano这个项目我会一直完善下去。我的目标是，在2022年，将EventOS Nano项目做成Gitee上的GVP项目，造福更多的嵌入式工程师。但目前已经完成的工作还远远不足，就我识别到的，将来需要完善的工作列举如下：
1. 良好的注释和文档
    + UM-001 快速入门文档
    + 【完成裸机】UM-002 移植文档（含裸机和RTOS上的移植）
    + UM-003 开发环境搭建说明
1. 【完成】将所有的变量和API以EventOS风格进行重构
1. 将C99标准实现的代码，修改为Clean C来实现。
1. 【完成】将构建工具修改为SCons
1. 增加内存管理功能，以支持任意长度的事件参数，修改掉原来的事件机制，优化RAM占用。
1. 【完成】将mdebug库删除，只保留断言接口，如果有日志必要，更换为elog库。（elog库，原名mlog，是我过去一直使用的日志库，整理后也会开源）
1. 【完成】将单元测试代码按照Unity框架进行重构
1. 对FSM模式的支持，以适用于最小资源的单片机ROM
1. 对HSM模式和发布-订阅模式的裁剪，以适用于最小资源的单片机ROM，优化RAM的占用
1. 对事件带参功能的裁剪，优化ROM的占用
1. 【完成】删除其中的行为树框架
1. 增加Doxygen风格的注释，并生成文档。
1. 对EventOS的eBridge（事件桥接）功能
1. 对ARM Cortex-M0 M3 M4 M7等单片机上的移植，增加对最常见型号单片机的支持，如STM32F103等。
    + ARM Cortex-M0
    + ARM Cortex-M3
    + ARM Cortex-M4
    + ARM Cortex-M7
    + 【完成】POSIX
    + FreeRTOS
    + 【完成】Test
    + Hello
    + Digital Watch（POSIX版）
    + Digital Watch（RTT版）
1. 对常见的IDE的支持
1. 对常见的RTOS的支持
1. 增加线程模式
1. 增加对RISC-V内核的支持
1. 网友的反馈与要求

### 联系方式
邮箱：event-os@outlook.com

除了邮箱之外，也可以加微信联系我，请注明**技术讨论**等相关字样。

![avatar](/documentation/figures/wechat.jpg)