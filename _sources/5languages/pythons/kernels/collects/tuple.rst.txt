元组()
============

.. note:: 也是一个List，差別只在不能做修改，一旦给定后，无法再进行增加 刪除 修改等操作，所以可以当作一个常数的List



创建为空的时候使用()，一个以上时括号可以省略，但是只有一个时最后一个逗号不可以省略::

    a = ()      # 空Tuples
    b = 'tem',  # b:(tem,) 括号可以省略，但是一个的時候逗号不能省略
    c = 'tem1', 'tem2', 'tem3'  # ('tem1', 'tem2', 'tem3')
    d, e, f = c   # d:'tem1', e:'tem2', f:'tem3'

任意交换变量间的值::

    a = '1'
    b = '2'
    c = '3'
    b, c, a = a, b, c
    print(a, b, c)    # 3 1 2


::

    zoo = ('wolf', 'elephant', 'penguin')
    new_zoo = ('monkey', 'dolphin', zoo)        #第三个元素是一个元组
    # 打印元组
    age = 22
    name = 'Swaroop'
    print('%s is %d years old' % (name, age))






