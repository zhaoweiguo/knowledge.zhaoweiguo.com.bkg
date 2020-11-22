.. _find:

find命令使用
==================
::

    find [路径] <表达式>

* 查找文件::

      -name <表达式> 根据文件名查找文件
      -perm mode,[-mode],[/mode],[+mode]
      -printf <format>
      -iname <表达式> 根据文件名查找文件,忽略大小写
      -path <表达式> 根据路径查找文件
      -ipath <表达式> 根据路径查找文件,忽略大小写
      -amin <分钟> 过去 N 分钟内访问过的文件
      -atime <天数> 过去 N 天内访问过的文件
      -cmin <分钟> 过去 N 分钟内修改过的文件
      -ctime <天数> 过去 N 天内修改过的文件
      -anewer <参照文件> 比参照文件更晚被读取过的文件
      -cnewer <参照文件> 比参照文件更晚被修改过的文件
      -size <大小> 根据文件大小查找文件,单位 b c w k M G
      -type <文件类型> 根据文件类型查找文件。b 块设备 c 字符设备 d 目录 p 管道文件 f 普通文件 l 链接 s 端口文件
      -user <用户名> 按归属用户查找文件
      -uid <uid> 按 UID 查找文件
      -group <群组名> 按归属群组查找文件
      -gid <gid> 按 GID 查找文件
      -empty 查找空文件




* 实例::

    find . -perm 664
    find . -perm -664

    //找
    find . -perm /220
    find . -perm /u+w,g+w
    find . -perm /u=w,g=w

    //找可被ower和group写的
    find . -perm -220
    find . -perm -g+w,u+w

    // 找出当前目录下普通文件列表
    find . -type f
    // 找出当前目录下文件夹列表
    find . -type d

    // 找出当前目录下更改时间在5日以前的文件并删除它们::
    find . -type f -mtime +5 -exec rm {} \;

    //使用正则
    find . -name "[a-z]*"    //找出以a-z开头的文件


    //可以通过下述指令查找硬链接
    find / -xdev -samefile /etc/resolv.conf

    // 指定路径为1的文件夹列表(即当前目录下文件夹列表,不包含.和..)
    find . -mindepth 1 -maxdepth 1 -type d



常见问题1::

  find: paths must precede expression: webfd
  Usage: find [-H] [-L] [-P] [-Olevel] [-D help|tree|search|stat|rates|opt|exec] [path...] [expression]

  // 原因
  即出现这个提示是因为星号代表为当前目录下所有的文件，然后被当做shell展开
  这就是网上说的多文件的查找的时候需要增加单引号
  This happens because *.c has been expanded by the shell resulting in find 

  // 解决方法
  $ find . -name '*.c' -print
  或
  $ find . -name \*.c -print


排除功能::

  % 在当前目录中，排除子目录source/ 和 blog/ ，查找所有的rst文件
  % -prune -o: 总计算为true,只展示此目录,不往此目录下继续执行
  find . -path "./blog" -prune -o -path "./source" -prune -o -name *.rst

  % 查找文件名为非*.c的文件
  find . ! -name "*.c" 

  % 
  find . -not -path  '*.svn*' -print  
  or
  find .  ! -path  '*.svn*' -print 


过滤::

    // 过滤指定文件夹
    files=( $(find . -name '*.go' -not -path './vendor/*') )
    
    // 过滤多个文件夹
    find . -name '*.go' -not -path  './cli/*' -not -path  './internal/*'













