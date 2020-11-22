zip()函数
#########

使用zip()可以对多组Object同时进行循环迭代::

    $ for day, fruit, drink, dessert in zip(days, fruits, drinks, desserts):
         print(day, ": drink", drink, "- eat", fruit, "- enjoy", dessert)
    
    Monday : drink coffee - eat banana - enjoy tiramisu
    Tuesday : drink tea - eat orange - enjoy ice cream
    Wednesday : drink beer - eat peach - enjoy pi


zip转换成list, dict::

    $ english = 'Monday', 'Tuesday', 'Wednesday'
    $ french = 'Lundi', 'Mardi', 'Mercredi'

    $ print('转换成list包tuple')
    $ print(list( zip(english, french) ))
    $ print('转换成Dictionarie')
    $ print(dict( zip(english, french) ))

    转换成list包tuple
    [('Monday', 'Lundi'), ('Tuesday', 'Mardi'), ('Wednesday', 'Mercredi')]
    转换成Dictionarie
    {'Monday': 'Lundi', 'Tuesday': 'Mardi', 'Wednesday': 'Mercredi'}








