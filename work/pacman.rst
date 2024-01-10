pacman管理
^^^^^^^^^^^^^^^^^^^^^^^


pamcan的key相关问题
----------------------

arch linux的博客章节, ::

    https://wiki.archlinux.org/title/Pacman/Package_signing#Change_keyserver

如果出现问题，可以把key重新初始化, ::

    sudo mv /etc/pacman.d/gnupg /tmp

    sudo pacman-key --init

    sudo pacman-key --populate

    sudo pacman -Sy archlinux-keyring && pacman -Su
