vscode使用技巧
^^^^^^^^^^^^^^^^^

vscode 调试运行在QEMU中的内核
===============================================

在linux工程的根目录创建.vscode目录，新建*launch.json*文件。
主要不要重复使用`target remote :1234`, 否则会出现提示 .. error::

    qemu-system-aarch64: QEMU: Terminated via GDBstub



.. code-block:: json

    "version": "0.2.0",
        "configurations": [
            {
                "name": "kernel-debug",
                "type": "cppdbg",
                "request": "launch",
                "program": "${workspaceFolder}/vmlinux",
                "stopAtEntry": true,
                "cwd": "${workspaceFolder}",
                "MIMode": "gdb",
                "miDebuggerPath": "/usr/bin/gdb-multiarch",
                "externalConsole": false,
                "problemMatcher": [],
            },
        ]
    }

vscode vim插件自动切换输入法
=======================================

以windows为例，首先从 `im-select`_ 下载im-select.exe, 然后参考 `vscode-vim`_ 来
@
以macos为例，我用的是macbook air M2，安装好im-select后，在命令行输入`im-select`, 然后看
到显示的是 *com.apple.keylayout.ABC*, 所以vscode的settings.json文件为 

.. code-block:: json
    
    "vim.autoSwitchInputMethod.enable": true,
    "vim.autoSwitchInputMethod.defaultIM": "com.apple.keylayout.ABC",
    "vim.autoSwitchInputMethod.obtainIMCmd": "/usr/local/bin/im-select",
    "vim.autoSwitchInputMethod.switchIMCmd": "/usr/local/bin/im-select {im}"


.. _vscode-vim: https://gitcode.com/VSCodeVim/Vim/overview
.. _im-select: https://gitcode.com/daipeihust/im-select/overview

vscode查看内核源码
===========================

用vscode查看内核源码，可以参考下面的博客 `Vscode+Clangd阅读linux内核源码`_

#. 在工程的根目录创建.clangd文件，填入以下内容： ::

        32位：
            CompileFlags:
            Add: --target=armv7-a
        64位：
            CompileFlags:
            Add: --target=aarch64-linux-gnu
            Remove: -mabi=lp64

.. _Vscode+Clangd阅读linux内核源码: https://blog.51cto.com/u_15948528/6027918

vscode设置
=====================

#. 主题颜色：*tokyo night pro navi*

vscode设置python虚拟环境
============================

#. 打开VSCode的设置（可以通过点击左下角的齿轮图标，然后选择“设置”）。
#. 搜索“Python: Select Interpreter”。
#. 选择“Auto-detect interpreter from the active environment”选项。

这样，VSCode将自动检测并使用当前激活的虚拟环境中的Python解释器。

