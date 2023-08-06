CUDA
^^^^^^^^^

基础知识
=============

kernel是device上线程中并行执行的函数，在并行执行时启动了很多线程。kernel启动的所有
线程称为grid。同一个grid共享相同的全局内存空间，grid是线程结构的第一层次，而一个grid
可以分为多个block，一个block又可以包括很多线程。grid和block被定义时为dim3类型的变量。
dim3可以看成是(x, y, z)的结构体变量，初始值为1。
