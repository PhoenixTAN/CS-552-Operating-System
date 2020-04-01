# Thread

## Why

paralize threads in different 

## Multithreading in user-lever v.s. Kernel-level

### Reference
https://zhuanlan.zhihu.com/p/26279675

### Multithreading in user level
用户级线程是指不需要内核支持而在用户程序中实现的线程，它的内核的切换是由用户态程序自己控制内核的切换，不需要内核的干涉。但是它不能像内核级线程一样更好的运用多核CPU。

优点：
1. 线程的调度不需要内核直接参与，控制简单。用户进程利用**线程库thread library**来控制用户线程。
2. 可以在不支持线程的操作系统中实现。
3. 同一进程中只能同时有一个线程在运行，如果有一个线程使用了系统调用而阻塞，那么**整个进程都会被挂起**，可以节约更多的系统资源。

缺点：
1. 一个用户级线程的阻塞将会引起整个进程的阻塞。
2. 用户级线程不能利用系统的多重处理，仅有一个用户级线程可以被执行。

### Multithreading in kernel level
内核级线程:切换由内核控制，当线程进行切换的时候，由用户态转化为内核态。切换完毕要从内核态返回用户态。可以很好的运用多核CPU，就像Windows电脑的四核八线程，双核四线程一样。

优点：
1. 当有多个处理机时，一个进程的多个线程可以同时执行。
2. 由于内核级线程只有很小的数据结构和堆栈，切换速度快，当然它本身也可以用多线程技术实现，提高系统的运行速率。

缺点：
1. 线程在用户态的运行，而线程的调度和管理在内核实现，在控制权从一个线程传送到另一个线程需要用户态到内核态再到用户态的模式切换，比较占用系统资源。（就是必须要受到内核的监控）


## light-weight process (LWP)
这种方案来解决，用户级多线程的blocking问题，当一个thread进行系统调用被阻塞时候，可以运行其他LWP来继续运行进程。

A means of achieving multitasking.

A LWP **runs in user space** on top of a single kernel thread and shares its address space and system resources with other LWPs within the same process.

LWPs (in systems where they are a separate layer) **bind to** kernel threads and provide a user-level context.
### Scheduling
While the user threading library will schedule user threads, the kernel will schedule the underlying **LWPs**.
