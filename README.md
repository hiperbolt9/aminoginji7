# 说明 Note
-------
本代码命名为EventOS Nano，作为我将在未来的开源分布式RTOS EventOS在小资源单片机（Cortex-M0/16/8位单片机）的精简版本。

这个代码的来历，是我在之前工作中做验证工作使用的，还有我业余做过一个开源的AGV控制器项目上使用的。是对QP状态机框架的精简实现，包含其大部分功能，只有一个源文件和头文件，便于嵌入任何工程。不仅如此，里面还实现了完整的行为树框架，并与状态机框架融为一体，后续考虑删除，但感兴趣的可以看看。在消费类机器人领域里，会经常使用。在目前的工作中，公司采购了正版的QP，这个代码在工作中也没有了用武之地，索性开源，做点贡献。

代码分为以下几个部分：
meow.c和meow.h分别是源文件和头文件，meow_config.h是设置头文件
port_linux.c port_mcu.c分别是Linux和单片机下的接口实现。里面包含了一个基于Linux的CMake工程，一个基于LPC4088的MDK工程。代码经过了充分的单元测试，且在若干个项目里进行了使用，可靠性久经考验，是有保证的。希望大家提出宝贵意见。

另外一个需要说明的是，在当前的dai

代码原来的名字叫Meow，是我老婆取的，因为她喜欢小猫的叫声。但这个名字多少有些不太严肃。末来这个项目我会一直完善下去，作为一个私有项目，这个源码让我受益良多，但作为一个开源项目，目前已经完成的工作还远远不足。就我识别到的，将来需要完善的工你列举如下：
1. 良好的注释和文档
2. 对ARM Cortex-M各型单片机上的移植
3. 对常见的IDE的支持
4. 对常见的RTOS的支持
5. 网友的反馈与要求

邮箱：event-os@outlook.com