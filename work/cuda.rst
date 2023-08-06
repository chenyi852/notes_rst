CUDA
^^^^^^^^^

基础知识
=============

kernel是device上线程中并行执行的函数，在并行执行时启动了很多线程。kernel启动的所有
线程称为grid。同一个grid共享相同的全局内存空间，grid是线程结构的第一层次，而一个grid
dim3可以看成是(x, y, z)的结构体变量，初始值为1。
grid(3,2)表示grid中x轴有3个block，y轴有2个block。
block(5.2)表示block中x轴有5个thread，y轴有3个thread。
GPU的一个核心组件是SM(Stream MultipleProcess), 包括CUDA核心，共享内存，寄存器等。
SM采用的是SIMT(single-instruction, mutiple-thread)架构，基本的执行单元是线程束
(wraps),线程束包含32个线程。这些线程同时执行指令，但是每个线程有自己的地址计数器和
寄存器状态，也有自己的执行路径。每个线程同时执行相同的指令，尽管线程束中的线程同时从
同一程序地址执行，但是可能具有不同的行为，比如遇到相同的分支，有些线程能进入分支，有些
不能，它们只能死等。GPU规定线程束中所有线程同一周期内只能执行相同的指令，线程束分化
会导致性能下降。grid和block只是按逻辑划分，一个kernel下的所有线程并不一定在物理上同时
并发执行。
CUDA 6.0之前的版本需要自己从host copy内存到device，而6.0之后的版本CUDA帮你copy。
