set{}
#####

.. note:: 集合就好比沒有value的dictionary，一样没有顺序，使用大括弧{}。使用set()可以转换其他类型至集合，dictionary转换至set只会保留key值。in也可以检查特定元素是否存在其中。

::

    empty_set = set()
    even_numbers = {0, 2, 4, 6, 8}
    print(empty_set, even_numbers)    # set() {0, 2, 4, 6, 8}

    print(set( 'letters' ))     # {'l', 's', 'e', 'r', 't'}
    print(set( ['D', 'A', 'P', 'M'] ))      # {'A', 'D', 'P', 'M'}
    print(set( ('U', 'Echoes', 'Atom') ))   # {'Echoes', 'Atom', 'U'}
    print(set( {'apple': 'red', 'orange': 'orange'} ))    # {'orange', 'apple'}






