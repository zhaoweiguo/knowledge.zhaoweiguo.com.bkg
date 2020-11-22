字典{}
============

.. note:: 为一种没有顺序的的容器，其使用的是大括弧{}，里面包含键值与值(key : value)




实例::

    ab = {
       'key1' : 'value1',
       'key2' : 'value2',
       'key3' : 'value3',
       'key4' : 'value4'
     }
     print("key1's value is %s" % ab['key1'])

     # 增加一条记录
     ab['key5'] = 'value5'

     # 删除一条记录
     del ab['key3']

     # 打印字典组中数据
     for key, value in ab.items():
         print ('key %s 的 value is %s' % (key, value))

     if 'key1' in ab:   # 或 ab.has_key('key1')
         print ("\nkey1的 value is %s" % ab['key1'])

实例::

    1. 初使化
    dic = { 'a':'v','b':'w', }  #最后一个逗号可以省略
    dic_ = { 'd':'y','c':'x' }  #最后一个逗号可以省略
    print(dic, dic_)

    2. 数组(tuple)转化为dict
    方法1:
    lol1 = [ ['a', 'b'], ['c', 'd'], ['e', 'f'] ]
    lol2 = [ ('a', 'b'), ('c', 'd'), ('e', 'f') ]
    lol3 = ( ['a', 'b'], ['c', 'd'], ['e', 'f'] )
    print(dict(lol1), dict(lol2), dict(lol3))

    方法2:
    tos1 = [ 'ab', 'cd', 'ef' ]
    tos2 = ( 'ab', 'cd', 'ef' )
    print(dict(tos1), dict(tos2))   # {'a': 'b', 'c': 'd', 'e': 'f'} {'a': 'b', 'c': 'd', 'e': 'f'}

    3. 替换
    3.1 dict元素替换
    print(dic_['c'])
    dic_['c'] = 'z'
    print(dic_['c'])

    3.2 dict替换
    dic.update(dic_)
    print(dic)

    4. 删除
    del dic['d']
    print(dic)

    5. 元素是否存在
    print('a' in dic)

    6. dict转化为数组(tuple)
    print(dic.keys())         # dict_keys(['a', 'b', 'c'])
    print(dic.values())       # dict_values(['v', 'w', 'x'])
    print(list(dic.items()))  # [('a', 'v'), ('b', 'w'), ('c', 'x')]

    7. 值传递vs引用传递
    7.1. 引用传递
    dic_new = dic
    dic_new['a'] = 'n'
    print(dic, dic_new)

    7.2. 值传递
    dic_cp = dic.copy()
    dic_cp['a'] = 'm'
    print(dic, dic_cp)








