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
   
        
