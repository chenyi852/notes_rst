linux内核新闻跟踪
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

2023-06-30
======================

#. NVDIA CUDA 12.2发布，支持linux HMM

   支持Linux kernel's Heterogeneous Memory Management(HMM), 主机和加速器间的内存
   可以无缝共享。cuda hmm 依赖6.1.24+或者 6.2.11+来使能某些必须的bits。

   在arm架构，在后端文件内存的GPU原子操作不支持，大页也不支持，fork系统调用也不
   支持。

2023-07-04
=======================

#. 去年USB4 v2.0的spec发布，TypeC线缆支持80Gbps的速率，一个方向120Gbps，另一个方向
   40Gbps。Intel贡献了USB4 v2的最初支持, 同时支持新的Intel Barlow Ridge discrete
   controller。

2023-9-4
=======================

如果结构体中的成员变量要被其他CPU访问，那么需要在成员变量后面加上cache line对齐的编译flag :: c

    atomic_t nr_running __cacheline_aligned_in_smp;

2023-9-13
======================

如果要打开/proc/sched_debug, 需要修改内核的配置文件，将CONFIG_SCHED_DEBUG改为y。

2023-10-08
=======================

workqueue的基本机制， `workqueue三种延迟`_
.. _`workqueue三种延迟`:
    https://zhuanlan.zhihu.com/p/648984958
