临时
##################

性能分析
========

* 测试目的：比较c,c++,node.js,erlang网络TCP读写性能
* 测试环境：linux
* 测试条件：Server为简单的TCP echo服务器,Server和Client运行在同一机器上，10000长连接,100活动连接
* 测试结果::

    c++ boost::asio
      connect=10000,active connect=100,req=148791,time=60,req/sec=2479.85,msec/req=40.343
    erlang  kernel-poll false
      connect=10000,active connect=100,req=979803,time=60,req/sec=16330,msec/req=6.12356
    node.js
      connect=10000,active connect=100,req=1378370,time=60,req/sec=22972.8,msec/req=4.35543
    c libevent
      connect=10000,active connect=100,req=3719106,time=60,req/sec=61985.1,msec/req=1.61258
    erlang kernel-poll true
      connect=10000,active connect=100,req=6377574,time=60,req/sec=106293,msec/req=0.939882



线上问题解决::

    - [ ] time_wait很奇怪的在超过5000后不再增长
        - 查看当前系统下所有连接状态的数：
        - netstat -n | awk '/^tcp/ {++S[$NF]} END {for(a in S) print a, S[a]}'
        - [root@aaa1 ~]# sysctl -a|grep net.ipv4.tcp_tw
        - [root@aaa1 ~]# vim /etc/sysctl.conf



