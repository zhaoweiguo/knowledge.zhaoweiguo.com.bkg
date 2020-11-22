列表[]
##############


List可以使用 [] 或是 list() 來创建空的，或是直接加入值进去，使用逗号区分即可。內容可以重复出现，且具有順序性::

    empty_list = []
    weekdays = ['Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday']
    big_birds = ['emu', 'ostrich', 'cassowary']

使用 list() 来作为转换其他类型到List::

    print(list('cat'))      # ['c', 'a', 't']

    a_tuple = ('ready', 'fire', 'aim')
    print(list(a_tuple))    # ['ready', 'fire', 'aim']

提取內容時跟字符串一样使用[ ]， index 从0开始，-1为最后一个::

    XD = ['a', 'b', 'c', 'd']
    print(XD[0])    # a
    print(XD[1])    # b
    print(XD[-1])   # d
    print(XD[-2])   # c

    XD[0] = 'QQ'

    print(XD[0:2])      # ['QQ', 'b']
    print(XD[2:-2])     # []
    print(XD[::2])      # ['QQ', 'c']

.. note:: List里面可以包含不同类型的Object，当然也包括List


可以使用List的內建函数append()来向后面添加元素:

+--------------------+--------------------------------------------------------------------------------+
| 语法               | 效果                                                                           |
+====================+================================================================================+
| list.extend()或 += | 合并list                                                                       |
+--------------------+--------------------------------------------------------------------------------+
| list.insert()      | 在指定位置插入元素，如果位置超过最大长度則放在最后面，故不会飞到很远去或出错。 |
+--------------------+--------------------------------------------------------------------------------+
| del Object         | 用来刪除某个位置的元素，剩余元素会自动往前填补                                 |
+--------------------+--------------------------------------------------------------------------------+
| list.remove()      | 用来移除指定元素                                                               |
+--------------------+--------------------------------------------------------------------------------+
| list.pop()         | 类似剪出的效果，可以將指定位置的元素剪出來，默认index为 -1                     |
+--------------------+--------------------------------------------------------------------------------+
| list.index()       | 找查指定元素第一次出现的index                                                  |
+--------------------+--------------------------------------------------------------------------------+
| in Object          | 判断指定元素是否存在                                                           |
+--------------------+--------------------------------------------------------------------------------+
| list.count()       | 计算指定元素出現次数                                                           |
+--------------------+--------------------------------------------------------------------------------+


实例1::

    XD = ['a', 'b']
    XD2 = ['e', 'f']

    XD.append('QQ~')    # ['a', 'b', 'QQ~']
    XD.extend(XD2)      # ['a', 'b', 'QQ~', 'e', 'f']
    XD += XD2           # ['a', 'b', 'QQ~', 'e', 'f', 'e', 'f']
    XD.append(XD2)      # ['a', 'b', 'QQ~', 'e', 'f', 'e', 'f', ['e', 'f']]
    XD.insert(2, 'c')   # ['a', 'b', 'c', 'QQ~', 'e', 'f', 'e', 'f', ['e', 'f']]
    XD.insert(500, 'ker')   # ['a', 'b', 'c', 'QQ~', 'e', 'f', 'e', 'f', ['e', 'f'], 'ker']
    del XD[8]           # ['a', 'b', 'c', 'QQ~', 'e', 'f', 'e', 'f', 'ker']
    XD.remove('e')      # ['a', 'b', 'c', 'QQ~', 'f', 'e', 'f', 'ker']
    QQ = XD.pop(3)      # ['a', 'b', 'c', 'f', 'e', 'f', 'ker'] QQ~

    print(XD.index('f'))    # 3
    print('ker' in XD)      # True
    print(XD.count('f'))    # 2

实例2::

    print(', '.join(['a', 'b', 'c']))       # a, b, c
    print(', '.join('abc'))                 # a, b, c
    print(', '.join(('a', 'b', 'c')))       # a, b, c
    print('a, b, c'.split(', '))            # ['a', 'b', 'c']

.. note:: 使用 '=' 设定变量则会是传址，等同于前面說的标签概念，把两张标签贴在同一个物件上(number or srting 除外) 这样当我改变Object后，则Object上所有的标签所指到的值都会跟着改变， 若要改成赋值的话可以使用copy() 、 list.list() 与 list[:] 来达到目的

实例3::

    a = [1, 2, 3]
    b = a

    # a变化, b也会变化
    a[0] = 4
    print(a, b)     # [4, 2, 3] [4, 2, 3]

    # a变化, c,d,e都不变
    c = a.copy()
    d = list(a)
    e = a[:]
    a[0] = 'surprises'
    print(a, b, c, d, e)    # ['surprises', 2, 3] ['surprises', 2, 3] [4, 2, 3] [4, 2, 3] [4, 2, 3]



::

    shoplist.sort()     #自排序

列表综合::

    listone = [2, 3, 4]
    listtwo = [2*i for i in listone if i > 2]
    print listtwo

    //結果
    [6, 8]


列表list::

    shoplist = ['apple', 'mango', 'carrot', 'banana']   #列表
    print '一共', len(shoplist), '个列表'   #打印列表个数
    for item in shoplist:        #打印列表中的各值
        print item
    shoplist.sort()     #自排序
    del shoplist[0]     #从列表中删除一条


序列::

    shoplist = ['apple', 'mango', 'carrot', 'banana']
    print('Item 0 is', shoplist[0])          #'apple'
    print('Item -2 is', shoplist[-2])        #'carrot'
    print('Item 1 to 3 is', shoplist[1:3])   #['mango', 'carrot']
    print('Item 0 to 3 is', shoplist[:3])   #['apple', 'mango', 'carrot']
    print('Item 1 to 3 is', shoplist[1:])   #['mango', 'carrot', 'banana']

    name = 'swaroop'
    print('characters 1 to 3 is', name[1:3])     #'wa'

    //参考:
    shoplist = ['apple', 'mango', 'carrot', 'banana']
    mylist = shoplist    #此乃引用
    mylist = shoplist[:] #此乃全复制
   










