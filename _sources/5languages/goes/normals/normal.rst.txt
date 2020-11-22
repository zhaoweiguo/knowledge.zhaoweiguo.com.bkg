常用
####

Code organization::

    Go programmers typically keep all their Go code in a single workspace.
    A workspace contains many version control repositories (managed by Git, for example).
    Each repository contains one or more packages.
    Each package consists of one or more Go source files in a single directory.
    The path to a package's directory determines its import path.

语言特点::

    自动垃圾回收
    更丰富的内置类型
    函数多返回值
    错误处理
    匿名函数与闭包
    类型与接口
    并发编程
    反射
    语言交互性

语法特点::

    函数头一字母大写时可以类外调用
    var hello string    变量声明
    := 不需要声明变量
    参数类型放在变量后面

工程管理::

    <gopath>目录结构: 
    |--README
    |--LICENSE
    |--<bin>
        |--calc
    |--<pkg>
        |--<linux_amd64>
           |--simplematch.a
    |--<src>
        |--<calc>
            |--calc.go'
        |--<simplepath>
            |--add.go
            |--add_test.go
            |--sqrt.go
            |--sqrt_test.go
         |--<github.com>
             |--<zhaoweiguo>
                 |--util.go


适合小白看的项目::

    推荐项目:

    beego
    BoltDB（不维护了，但是代码不多，注释比较详细，作为学习容易入门）
    urfave/cli
    grpc-gateway
    grpc-go









