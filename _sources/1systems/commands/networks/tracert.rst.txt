.. _tracert:

tracert命令
##################

::

    tracert <ip> or <domain>

    traceroute -l <domain>

    tracepath <domain>  //在ubuntu下可代替tracert的命令

    $ mtr <domain>      //交互式命令, 每秒刷新一次, 可以使用交互命令 i 调整时间



假双线查询::

  使用如下命令查看ip转向:
    $ tracert <ip>
    $ tracert <domain>
    or
    $ mtr <domain>
    or
    tracepath <domain>

  进入服务器使用如下命令查看双线映射路由表:
    route -e
    or
    netstat -r

