python
^^^^^^^^^^^

venv
===========

#. 安装
   python 3.6的版本已经默认安装。

#. 创建虚拟环境

   假设我们要在当前目录创建虚拟环境::
        
        python3 -m venv test_env

#. 启用虚拟环境

   在linux 和macos的shell下， 执行下面的命令::

        source ./test_env/bin/active

#. 安装依赖包

   虚拟环境启用后，直接用pip安装命令即可。

   在Linux和Mac系统上，安装的包放在./test_env/lib/pythonx.x/site-packages 目录下.

#. 退出虚拟环境

   执行下面的命令即可::

        deactive
   
debug
================

#. 输出调用栈。如果python遇到错误，它就会生成一些错误信息，称为‘反向跟踪’。反向跟踪包含
   了出错消息、导致该错误的代码行号，以及导致该错误的函数调用链。
   .. code-block:: python

        import traceback

        try:
                raise Exception('This is the error message.')
        except:
                errorFile = open('errorInfo.txt', 'w')
                errorFile.write(traceback.format_exec())
                errorFile.Close()
                print('The traceback info was written to errorInfo.txt')
