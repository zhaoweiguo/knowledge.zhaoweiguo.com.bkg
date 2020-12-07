其他命令临时地
##############

pycopy & pbpaste
================

* linux版: https://www.ostechnix.com/how-to-use-pbcopy-and-pbpaste-commands-on-linux/

使用::

    // mac 自带命令
    pbcopy < ~/.ssh/id_rsa.pub
    grep "<keyword>" | pbcopy

.. note::  这个命令好用，比 linux 下此命令好用。可以完美与 gui 接合



技巧
====

::

    ctrl + r

.. image:: /images/linuxs/shell_skill_C_r.gif


Fast Navigation::

    Ctrl + a: Move to the beginning of the command.
    Ctrl + e: Move to the end of the command.
    Ctrl + u: Delete everything to the right of the cursor.
    Ctrl + w: Delete a word to the left.
    Ctrl + d: Delete a Character to the right.
    Cmd + w: Closing a Tab
    Cmd + t: Opening a new Tab
    
    The following shortcuts doesn't come preloaded, you need to configure them from `here <https://coderwall.com/p/h6yfda/use-and-to-jump-forwards-backwards-words-in-iterm-2-on-os-x>`_ :
    option + ←: Move one word to the left
    option + →: Move one word to the right.

iTerm快捷键::

    时间线: Shift + Cmd + E


    自定义: Ctl + Cmd + Z



其他
====

- 摘自: https://medium.com/swlh/my-favorite-cli-tools-c2fa484cee52
- mac 工具：
    - 窗口管理：
        - https://github.com/rxhanson/Rectangle
        - https://github.com/ianyh/Amethyst
        - 类似Magnet
    - [x] 记忆专用
        - 记忆卡片: https://apps.ankiweb.net/
    - gif 生成工具
        - https://www.cockos.com/licecap/
    - 替换 find
        - fda='fd -IH'
        - https://github.com/sharkdp/fd
        - brew install fd
    - 替换 grep
        - https://github.com/BurntSushi/ripgrep
        - It skips files ignored by .gitignore and hidden ones
    - 比 htop 更全，和 htop 互补
        - https://nicolargo.github.io/glances/
        - https://github.com/nicolargo/glances
        - Glances is a cross-platform system monitoring tool written in Python.
- docker 工具
    - ctop
        - https://github.com/bcicen/ctop
        - brew install ctop
    - lazydocker
        - https://github.com/jesseduffield/lazydocker
        - The lazier way to manage everything docker
        - brew install lazydocker
        - [更新版]brew install jesseduffield/lazydocker/lazydocker
- 其他
    - [x] asciinema
        - https://asciinema.org/
        - brew install asciinema
        - Record and share your terminal sessions, the right way.
- 小工具
    - lolcat
    - colordiff
        - https://www.colordiff.org/
    - diff-so-fancy
        - https://github.com/so-fancy/diff-so-fancy
    - bat
        - 代替 cat 和 less(?)
    - httpie
        - https://httpie.org/
        - 更直观
    - exa
        - 代替 ls
        - https://the.exa.website/
- 开发
    - litecli
        - https://litecli.com/
        - SQLite
        - With the auto-completion and syntax highlighting
    - pgcli
        - https://www.pgcli.com/
        - PostgreSQL



