代码导航
^^^^^^^^^^^^^^^^^^^^^

vscode+clangd阅读Linux内核代码
==================================================

如果用vscode + C++的插件看代码，CPU占用比较大，而且很多无关代码都加入到里面了。
本方案是通过vscode + ssh 远程到服务器查看代码。

安装vscode+clangd
----------------------------

参考其他教材安装即可，clangd为vscode的插件。如果服务器的网络顺畅，会自动安装
（clangd language server），如果下载失败，可以手动下载安装。

安装bear
------------------

clangd的解析函数功能依赖于compile_commands.json文件，该文件不是手写的，而是可以通过bear工具在编译内核时自动生成。对于ubuntu，可用如下命令进行安装。对手ubuntu, 可以通过以下命令安装::shell

sudo apt download bear

bear安装好以后就可以生成compile_commands.json文件了，命令是::shell

bear -- make Image -j`nproc`

创建.clangd
----------------------

在vscode打开的源代码的根目录创建一个名为.clangd的文件，区分32位arm和64位arm，其内容如下::

32位：
    CompileFlags:
      Add: --target=armv7-a
64位：
    CompileFlags:
      Add: --target=aarch64-linux-gnu
      Remove: -mabi=lp64


代码解析
---------------

如果clangd正常工作，在vscode打开源代码并且随便点击一个c文件后会开始解析项目，在工作路径下生成.cache文件夹，.cache文件夹下有当前每个被编译进去的文件对应的index；如果index文件数量太少（通常在800以上），几乎可以断定工作不正常，此时需要看vscode的解析状态来进一步分析原因。最终效果如下：可以进行函数跳转，过滤掉了没有被编译的函数，同时在分析函数指针时也少了很多干扰。

如果clangd正常工作，在vscode打开源代码并且随便点击一个c文件后会开始解析项目，在工作路径下生成.cache文件夹，.cache文件夹下有当前每个被编译进去的文件对应的index；如果index文件数量太少（通常在800以上），几乎可以断定工作不正常，此时需要看vscode的解析状态来进一步分析原因。最终效果如下：可以进行函数跳转，过滤掉了没有被编译的函数，同时在分析函数指针时也少了很多干扰。


本文档参考自 [嵌入式打工仔文章]_。

.. [嵌入式打工仔文章] 《Vscode+Clangd 阅读linux内核源码》 https://blog.51cto.com/u_15948528/6027918
