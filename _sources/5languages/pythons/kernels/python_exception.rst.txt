异常相关
=============


异常::

    # 处理异常:
    try:
        s = raw_input('输入 --> ')
    except EOFError:
        print '\n 产生EOF错误'
        sys.exit() # exit the program
    except:
        print '\n产生其他错误'


引发异常::

    class ShortInputException(Exception):
        '''自定义的异常——ShortInputException.'''
        def __init__(self, length, atleast):
            Exception.__init__(self)
            self.length = length
            self.atleast = atleast

        try:
            s = raw_input('输入 --> ')
            if len(s) < 3:
                raise ShortInputException(len(s), 3)

        except EOFError:
            print '\nEOF错误产生?'
        except ShortInputException, x:
            print 'ShortInputException: 输入长度为 %d, 规定至少为 %d' % (x.length, x.atleast)
        else:
            print '无错误产生.'

