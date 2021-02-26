内置函数(标准库函数)
####################


::

    int(x)    # convert to Integers
    str(x)    # convert to Strings
    list(x)   # convert to List



exec和eval语句::

    exec 'print "Hello World"'    # fail
    eval('2*3')

assert语句::

    # assert语句用来声明某个条件是真的
    # 当assert语句失败的时候，会引发一个AssertionError
    mylist = ['item']
    assert len(mylist) >= 1
    mylist.pop()
    assert len(mylist) >= 1
    # Traceback (most recent call last):
    #  File "<stdin>", line 1, in ?
    #  AssertionError


repr函数(用来取得对象的规范字符串表示)::

    i = []
    i.append('item')
    # repr函数
    repr(i)
    # 反引号（也称转换符）可以完成相同的功能
    `i`




::

   __init__(self，...),      这个方法在新建对象恰好要被返回使用之前被调用
   _del__(self),             恰好在对象要被删除之前调用
   __str__(self),            在我们对对象使用print语句或是使用str()的时候调用
   __lt__(self，other),      当使用 ``小于`` 运算符（<）的时候调用
   __getitem__(self，key),   使用x[key]索引操作符的时候调用
   __len__(self),            对序列对象使用内建的len()函数的时候调用


内置函数::

  open(filename[, mode[, bufsize]])
  参数:
   r:read
   a:append
   w:write
   b:binary(text mode will treat ``\n``, ``\r\n``, ``\r`` different in different system)

   file.tell()
   返回file’s current position, 同 stdio‘s ftell()

   file.seek(offset[, whence])
       f.seek(2, os.SEEK_CUR)     //advances the position by two
       f.seek(-3, os.SEEK_END)    //sets the position to the third to last

lambda
======

可以这样认为，lambda 作为一个表达式，定义了一个匿名函数，如::

    例:
    g = lambda x:x+1

    可看作:
    def g(x):
         return x+1

.. note:: 　　lambda 定义了一个匿名函数。lambda 并不会带来程序运行效率的提高，只会使代码更简洁。


全局函数方便使用的，filter, map, reduce::

    foo = [2, 18, 9, 22, 17, 24, 8, 12, 27]
    print(filter(lambda x: x % 3 == 0, foo))
    print(map(lambda x: x * 2 + 10, foo))
    print(reduce(lambda x, y: x + y, foo))

实例::

    def make_repeater(n):
        return lambda s: s*n

    twice = make_repeater(2)

    print(twice('word'))






