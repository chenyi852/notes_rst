linux内核新闻跟踪
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

2023-06-30
======================

#. NVDIA CUDA 12.2发布，支持linux HMM

   支持Linux kernel's Heterogeneous Memory Management(HMM), 主机和加速器间的内存
   可以无缝共享。cuda hmm 依赖6.1.24+或者 6.2.11+来使能某些必须的bits。

   在arm架构，在后端文件内存的GPU原子操作不支持，大页也不支持，fork系统调用也不
   支持。
