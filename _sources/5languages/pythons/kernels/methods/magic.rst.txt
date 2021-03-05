魔法方法
########


::

   __init__(self，...),      这个方法在新建对象恰好要被返回使用之前被调用
   _del__(self),             恰好在对象要被删除之前调用
   __str__(self),            在我们对对象使用print语句或是使用str()的时候调用
   __lt__(self，other),      当使用 ``小于`` 运算符（<）的时候调用
   __getitem__(self，key),   使用x[key]索引操作符的时候调用
   __len__(self),            对序列对象使用内建的len()函数的时候调用



比较用::

    方法名称                       使用
    __eq__(self, other)         self == other
    __ne__(self, other)         self != other
    __lt__(self, other)         self < other
    __gt__(self, other)         self > other
    __le__(self, other)         self <= other
    __ge__(self, other)         self >= other

数学用::

    方法名                         使用
    __add__(self, other)        self + other
    __sub__(self, other)        self - other
    __mul__(self, other)        self * other
    __floordiv__(self, other)   self // other
    __truediv__(self, other)    self / other
    __mod__(self, other)        self % other
    __pow__(self, other)        self ** other

其他常用::

    方法名             使用
    __str__(self)     str(self)
    __repr__(self)    repr(self)
    __len__(self)     len(self)

采用一般方法写法::

    class Word():
        def __init__(self, text):
            self.text = text

        def equals(self, word2):
            return self.text.lower() == word2.text.lower()

    #创建3个字符Object
    first = Word('ha')
    second = Word('HA')
    third = Word('eh')

    #进行比较
    first.equals(second)  #True
    first.equals(third)   #False

采用特殊方法写法::

    class Word():
        def __init__(self, text):
            self.text = text

        def __eq__(self, word2):
            return self.text.lower() == word2.text.lower()

    #创建3个字符对象
    first = Word('ha')
    second = Word('HA')
    third = Word('eh')

    #进行比较
    first == second  #True
    first == third   #False







