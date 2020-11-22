etcdctl命令 [1]_
################


数据库操作
==========

put::

    $ etcdctl put /testdir/testkey "Hello world"
    OK

get::

    $ etcdctl put testkey hello
    OK
    $ etcdctl get testkey
    testkey
    hello

del::

    $ etcdctl del testkey
    1


watch::

    监测一个键值的变化，一旦键值发生更新，就会输出最新的值
    例如，用户更新 testkey 键值为 Hello world

    $ etcdctl watch testkey
    PUT
    testkey
    2

member::

    通过 list、add、update、remove 命令列出、添加、更新、删除 etcd 实例到 etcd 集群中
    例如本地启动一个 etcd 服务实例后，可以用如下命令进行查看

    $ etcdctl member list
    422a74f03b622fef, started, node1, http://172.16.238.100:2380, http://172.16.238.100:23














.. [1] https://github.com/etcd-io/etcd/blob/master/Documentation/dev-guide/interacting_v3.md