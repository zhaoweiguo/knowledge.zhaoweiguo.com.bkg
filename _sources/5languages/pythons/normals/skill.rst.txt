技巧
####


python中获取当前位置所在的行号和函数名::

    def get_cur_info(): 
        print sys._getframe().f_code.co_name 
        print sys._getframe().f_back.f_lineno 

    get_cur_info()  



python使用小技巧::

  shell> python -v
  python>>> import sys
  python>>> print sys.path    # 打印系统安装路径

::

    $ print([number for number in range(1,6)])
    [1, 2, 3, 4, 5]

# 可以对expression部分进行运算处理::

    $ print([number*2 - 3 for number in range(2,5)])
    [1, 3, 5]

# 可以放置if判断式::

    $ print([number for number in range(1,6) if number % 2 == 1])
    [1, 3, 5]

# 嵌套循环也可以使用隐含式::

    $ cells = [(r,c) for r in range(1, 4) for c in range(1, 3)]
    $ for cell_r, cell_c in cells:
        print(cell_r, cell_c)
   
    1 1
    1 2
    2 1
    2 2
    3 1
    3 2

# 计算一个单字里字母的出现的次数::

    $ word = 'letters'
    $ letter_counts={letter:word.count(letter) for letter in set(word) if letter.lower() not in 'aeiou'}
    $ print(letter_counts)
    {'l': 1, 's': 1, 'r': 1, 't': 2}

set推导式::

    $ print({number for number in range(1,6) if number % 3 == 1})
    {1, 4}

使用 * 与 ** 收集位置参数与关键字参数::

    说明:
    *收集而成的参数会以Tuples储存
    **收集到的会以Dictionary储存

    $ print('\n混合位置参数使用，剩下的都给收集器')
    $ def print_more(required1, required2, *args):
        print('Need this one:', required1)
        print('Need this one too:', required2)
        print('All the rest:', args)
   
    $ print_more('cap', 'gloves', 'scarf', 'monocle', 'mustache wax')

    混合位置参数使用，剩下的都给收集器
    Need this one: cap
    Need this one too: gloves
    All the rest: ('scarf', 'monocle', 'mustache wax')

    $ def print_kwargs(**kwargs):
         print('Keyword arguments:', kwargs)
    
    $ print_kwargs(wine='merlot', entree='mutton', dessert='macaroon')

    Keyword arguments: {'wine': 'merlot', 'entree': 'mutton', 'dessert': 'macaroon'}
















