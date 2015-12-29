# 重定向与管道

## 文件描述符

**文件描述符**（File descriptor）是计算机科学中的一个术语，是一个用于表述指向文件的引用的抽象化概念。

文件描述符在形式上是一个非负整数。实际上，它是一个索引值，指向内核为每一个进程所维护的该进程打开文件的记录表。当程序打开一个现有文件或者创建一个新文件时，内核向进程返回一个文件描述符。在程序设计中，一些涉及底层的程序编写往往会围绕着文件描述符展开。但是文件描述符这一概念往往只适用于UNIX、Linux这样的操作系统。

> 更多文件描述符的操作参考维基百科 [文件描述符](https://zh.wikipedia.org/wiki/%E6%96%87%E4%BB%B6%E6%8F%8F%E8%BF%B0%E7%AC%A6)

## Linux的默认I/O

Linux shell（比如 Bash）接收或发送序列和字符串流 形式的输入或输出。每个字符都独立于与之相邻的字符。字符没有被组织成结构化记录或固定大小的块。不管实际的字符串流进入或来自文件、键盘、显示窗口或其他 I/O 设备，都使用文件 I/O 技术来访问流。Linux shell 使用 3 种标准的 I/O 流，每种流都与一个文件描述符相关联：

1. ``stdout`` 是标准输出流，它显示来自命令的输出。它的文件描述符为 1。
2. ``stderr`` 是标准错误流，它显示来自命令的错误输出。它的文件描述符为 2。
3. ``stdin`` 是标准输入流，它为命令提供输入。它的文件描述符为 0。

输入流通常通过终端击键为程序提供输入。输出流通常向终端输出文本字符。最初的终端是 ASCII 打字机或显示终端，但现在更多是指图形桌面上的文本窗口。

![](http://ryanstutorials.net/linuxtutorial/img/streams.png)

本章将重点探讨重定向与管道的相关内容。