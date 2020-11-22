.. _python_simple:

python收集
====================

import相关::

    # 此模块import它上一层的模块
    import sys
    sys.path.append("..")

    //实例:
    import pymongo

运算符与表达式::

    ** 幂 
    // 取整除
    %  取模


控制流基本格式::

    //if操作
    if guess == number:
        print 'a1'
    elif guess == number2:
        print 'a2'
    else:
        print 'a3'

    //while操作
    while True:
        s = raw_input('Enter something : ')
        if s == 'quit':
            break
        elif s == 'continue':
            continue

    //for操作
    for i in range(1, 5):
        print i
    else:
        print i+1
    //


    range(1, 5)
    // [1, 2, 3, 4]


python函数::

    如果一个Python函数、类方法或属性的名字以两个下划线开始(但不是结束), 它是私有的
    类方法或者是私有 (只能在它们自已的类中使用) 或者是公有 (任何地方都可使用)

    def <funName>():    #定义
    ... ...

    <funName>() # 调用


实例1::

    def func(x):
        global y        #全局变量
        print 'x is', x #打印变量
        x = 2    #修改变量

    x = 50  #函数外修改
    func(x) #执行函数

    //——使用默认参数值::
    def say(message, times = 1):
        print message * times

    say('Hello')
    say('World', 5)

    //实例3——ifelse、return語句::
    def maximum(x, y):
        if x > y:
            return x
        else:
            return y
    print maximum(2, 3)

DocStrings(文档字符串, 它通常被简称为 ``docstrings``, DocStrings是一个重要的工具, 由于它帮助你的程序文档更加简单易懂, 你应该尽量使用它)::

    def printMax(x, y):
        '''Prints the maximum of two numbers.
        The two values must be integers.'''     # 文档字串
        x = int(x) # convert to integers, if possible
        y = int(y)

        if x > y:
            print x, 'is maximum'
        else:
            print y, 'is maximum'

        printMax(3, 5)
        print printMax.__doc__  #文档打印


模块::

    import sys
    print 'The command line arguments are:'
    for i in sys.argv:
        print i
    print '\n\nThe PYTHONPATH is', sys.path, '\n'


    如果你想要直接输入argv变量, 而不用每次使用它时打sys:
    from sys import argv

    //dir函数:
    import sys
    dir(sys)    # get list of attributes for sys module



输入/输出::

    # 往文件里写数据
    f = file('poem.txt', 'w')
    f.write("<...>")
    f.close()

    # 读文件里的数据
    f = file('poem.txt')
    while True:
        line = f.readline()
        if len(line) == 0: # 长度为0意味着EOF
            break
        print line,
    f.close()

    # file.seek(0)的使用:
    file.seek(0)是重新定位在文件的第0位及开始位置 
    file = open("test.txt","rw")  #注意这行的变动
    file.seek(3)  #定位到第3个
    for i in file:
        print i
    # 现在到了最后一位了
    for i in file:
        print i
    # 不会显示任何结果
    file.seek(0) #定位到第0个
    for i in file:
        print i


储存器(Python提供一个标准的模块，称为pickle。使用它你可以在一个文件中储存任何Python对象，之后你又可以把它完整无缺地取出来。这被称为 持久地 储存对象)::

    # 储存与取储存
    import cPickle as p

    shoplistfile = 'shoplist.data'      #文件名
    shoplist = ['apple', 'mango', 'carrot']     #列表内容
    f = file(shoplistfile, 'w')   # 以写的方式打开文件
    p.dump(shoplist, f)           # 把列表内容存放到之前指定的文件中
    f.close()

    del shoplist
    f = file(shoplistfile)      # 以读的方式打开文件
    storedlist = p.load(f)      # 打开文件
    print storedlist



