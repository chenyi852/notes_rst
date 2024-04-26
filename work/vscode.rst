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

以windows为例，首先从 `im-select`_ 下载im-select.exe, 然后参考 `vscode-vim_` 来

.. _vscode-vim: https://gitcode.com/VSCodeVim/Vim/overview
.. _im-select: https://gitcode.com/daipeihust/im-select/overview