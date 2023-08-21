linux使用指南
^^^^^^^^^^^^^^^^^^^^^^^^

系统工具
========================

安装autojump
-------------

ubuntu
**************

首先安装autojump软件包, ::

    sudo apt install autojump

在bashrc或者zshrc中添加 ::

    [ -f /usr/share/autojump/autojum.sh ] && source /usr/share/autojump/autojump.sh

网络工具
=======================

安装ssh
---------------

ssh常用于客户端登录到服务器

arch linux
******************

安装软件包后，需打开服务, ::

    # 安装ssh
    pacman -Syy openssh
    # 启动服务
    systemctl start sshd
    # 开机启动
    systemctl enable sshd.service   


截图软件
============

flameshot
-------------

启动GUI工具命令为 flameshot GUI

笔记软件
=============

nb
---------

一个可以在命令行工作的软件
