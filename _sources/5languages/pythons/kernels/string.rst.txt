.. _python_string:

python字符串处理
################

字符串提取
==========

提取方法如下::

    用法                      说明
    [ : ]                   提取全部
    [start : ]              提取 start 至結束
    [ : end]                提取开头到 end - 1
    [start : end]           提取 start 至 end - 1
    [start : end : step]    提取 start 至 end - 1，间隔为step (step为负的时候则从右边开始，start与end需反过来摆放)


实例1::

    str = '12345678'
    print str[0:1]
    >> 1             # 输出str位置0开始到位置1以前的字符
    print str[1:6]
    >> 23456         # 输出str位置1开始到位置6以前的字符
    num = 18
    str = '0000' + str(num)# 合并字符串
    print str[-5:]   # 输出字符串右5位
    >> 00018

实例2-索引::

    a = 'bcd'    
    print(a[0]) # 'b' 
    print(a[-1]) # 'd'

实例3-反序排列::

    a = 'abcde'
    print(a[::-1]) #'edcba' 可以变成反序排列
    print(a[-2:0:-1]) #'dcb'



字符串替换
==========

::

    str = 'akakak'
    str = str.replace('k',' 8')      # 将字符串里的k全部替换为8
    print str
    >> 'a8a8a8'# 输出结果

实例1::

    name = 'Henny'
    #name[0] = 'P' #错误!!!!!!
    a = name.replace('H', 'P') #'Penny'
    print(a)
    print('P' + name[1:]) #'Penny'



字符串查找
==========

::

    str = 'a,hello'
    print str.find('hello')      # 在字符串str里查找字符串hello
    >> 2# 输出结果

获取字符串长度::

    a = 'abc'
    print(len(a))

检查开头結束字串是否为特定字串，返回True或False::

    poem = 'abcdef'
    print(poem.startswith('ab'))    # True
    print(poem.endswith('eef'))     # False

查搜索索引, 查搜索串个数::

    poem = 'abcdefbcd'
    print(poem.find('bc'))      # 1(第一次出现搜索字串的index)
    print(poem.rfind('bc'))     # 6(最后一次出现搜索字串的index)
    print(poem.count('bc'))     # 2(查询字串出现次数)

查询字符串中是否都是字母或数字，返回True或False::

    poem = 'abc@def'
    print(poem.isalnum())   # False
    
    poem = 'abcdef23'
    print(poem.isalnum())   # True


字符分割
========

实例1::

    str = 'a,b,c,d'
    strlist = str.split(',')     # 用逗号分割str字符串，并保存到列表

实例2::

    todos = 'get gloves,get mask,give cat vitamins,call ambulance'
    print(todos.split(','))
    print(todos.split())   # 默认会切割\n(换行) 、 \t(tab)与空格三种


字符合并
========

实例1::

    sep=":"
    items=sep.join(strlist)
    print items       # 'a:b:c:d'

实例2::

    crypto_list = ['Yeti', 'Bigfoot', 'Loch Ness Monster']
    print(', '.join(crypto_list))

建立重复字符串::

    print('a' * 5) # 'aaaaa'


其他
====

字符串的方法::

    name = 'Swaroop'
    if name.startswith('Swa'):
        print('Yes, the string starts with "Swa"')
    if 'a' in name:
        print('Yes, it contains the string "a"')
    if name.find('war') != -1: #得到字符串里含有子字符串对应的位置,没有为-1
        print('Yes, it contains the string "war"')

    delimiter = '_*_'
    mylist = ['Brazil', 'Russia', 'India', 'China']
    print delimiter.join(mylist)  # Brazil_*_Russia_*_India_*_China

方便的string內建function::

    setup = 'a duck goes into a bar...'
    print(setup.strip('.'))                      #刪除結尾特定符号 'a duck goes into a bar'
    print(setup.capitalize())                    #字串第一個字符大写 'A duck goes into a bar...'
    print(setup.title())                         #每个单词的首字母大写'A Duck Goes Into A Bar...'
    print(setup.upper())                         #全部大写 'A DUCK GOES INTO A BAR...'
    print(setup.lower())                         #全部小写'a duck goes into a bar...'
    print(setup.swapcase())                      #大小写交换 'A DUCK GOES INTO A BAR...'
    print(setup.center(30))                      #将字符串中心移动至30个字符的中间 '  a duck goes into a bar...   '
    print(setup.ljust(30))                       #左对齐 'a duck goes into a bar...     '
    print(setup.rjust(30))                       #右对齐 '     a duck goes into a bar...'
    print(setup.replace('duck', 'marmoset'))     #'a marmoset goes into a bar...'
    print(setup.replace('a ', 'a famous ', 100)) #只替换前100个'a '



说明::

    单引号指示字符串,所有的空白，即空格和制表符都照原样保留
    双引号中的字符串与单引号中的字符串的使用完全相同
    三引号，你可以指示一个多行的字符串;在三引号中自由的使用单引号和双引号

    自然字符串——不需要如转义符那样的特别处理的字符串:

    r"Newlines are indicated by \n"
    # '\\1'或r'\1'一样

    Unicode字符串——国际文本的标准方法(要在字符串前加上前缀u或U)::

    u"This is a Unicode string."







