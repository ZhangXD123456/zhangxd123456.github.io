---
title: 什么是 FreeRTOS
date: '2022-08-25 16:00'
categories: ESP8266
tags:
    - ESP8266
    - 硬件编程
---
# 什么是FreeRTOS

> 1.Free 即免费的，RTOS 全称是 Real Time Operating System，中文就是实时操作系统。注意，RTOS 不是指某一个确定的系统，而是指一类系统。比如 uC/OS，FreeRTOS，RTX，RT-Thread 等这些都是 RTOS 类操作系统。
> 2.操作系统允许多个任务同时运行，这个叫做多任务。实际上，一个处理器核心在某一时刻只能运行一个任务。操作系统中任务调度器的责任就是决定在某一时刻究竟运行哪个任务。任务调度在各个任务之间的切换非常快，就给人们造成了同一时刻有多个任务同时运行的错觉。
> 3.某些操作系统给每个任务分配同样的运行时间，时间到了就轮到下一个任务，比如Unix 操作系统。 FreeRTOS 操作系统则是由用户给每个任务分配一个任务优先级，任务调度器就可以根据此优先级来决定下一刻应该运行哪个任务。
> 4.FreeRTOS 是 RTOS 系统的一种，FreeRTOS 十分的小巧，可以在资源有限的微控制器中运行，当然，FreeRTOS 不仅局限于在微控制器中使用。但从文件数量上来看 FreeRTOS 要比uC/OSII 和 uC/OSIII 小的多。
>

FreeRTOS资料

[www.freertos.org](http://www.freertos.org/)