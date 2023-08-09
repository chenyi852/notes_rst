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

当一个kernel被执行时，它的grid中的线程块被分配到SM上，一个线程块只能在一个SM上被调度。
SM一般可以调度多个线程块，这要看SM本身的能力。
block大小为32的倍数，但是一个block只能在一个SM上被调度，而一个线程束包含32个线程，因此
如果block的32XN个线程，那么SM就要分配N个线程束，但是SM要为每个线程块分配贡献内存，为
每个线程束中的线程分配独立的寄存器。

CUDA 6.0之前的版本需要自己从host copy内存到device，而6.0之后的版本CUDA帮你copy。

执行流程如下：

#. 分配host内存，并进行数据初始化；
#. 分配device内存，并从host将数据拷贝到device上；
#. 调用CUDA的核函数在device上完成指定的运算；
#. 将device上的运算结果拷贝到host上；
#. 释放device和host上分配的内存。

上面流程中最重要的一个过程是调用CUDA的核函数来执行并行计算，kernel是CUDA中一个重要的
概念，kernel是在device上线程中并行执行的函数，核函数用__global__符号声明，在调用时
需要用<<<grid, block>>>来指定kernel要执行的线程数量，在CUDA中，每一个线程都要执行
核函数，并且每个线程会分配一个唯一的线程号thread ID，这个ID值可以通过核函数的内置变量
threadIdx来获得。

由于GPU实际上是异构模型，所以需要区分host和device上的代码，在CUDA中是通过函数类型
限定词开区别host和device上的函数，主要的三个函数类型限定词如下：

#. __global__：在device上执行，从host中调用（一些特定的GPU也可以从device上调用），
   返回类型必须是void，不支持可变参数参数，不能成为类成员函数。注意用__global__定义的
   kernel是异步的，这意味着host不会等待kernel执行完就执行下一步。
#. __device__：在device上执行，单仅可以从device中调用，不可以和__global__同时用。
#. __host__：在host上执行，仅可以从host上调用，一般省略不写，不可以和__global__同时用，
   但可和__device__，此时函数会在device和host都编译。