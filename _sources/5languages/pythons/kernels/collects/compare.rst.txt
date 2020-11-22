不同集合对比
############


列表(list)与Tuples
==================

两者差异在于::

    1. List可以改变其內容，增減长度 or 替换等等皆可以
    2. Tuples一旦赋值之后，就不能再修改
    3. 以性能和内存使用量来说，Tuples皆较佳

list,tuple,dict实例::

        marx_list = ['Groucho', 'Chico', 'Harpo']
        marx_tuple = 'Groucho', 'Chico', 'Harpo'
        marx_dict = {'Groucho': 'banjo', 'Chico': 'piano', 'Harpo': 'harpo'} 
        print(marx_list[2])         # Harpo
        print(marx_tuple[2])        # Harpo
        print(marx_dict['Harpo'])   # Harpo

集合实例
======================

不同容器之间的使用差别::

    marx_list = ['Groucho', 'Chico', 'Harpo']
    marx_tuple = 'Groucho', 'Chico', 'Harpo'
    marx_dict = {'Groucho': 'banjo', 'Chico': 'piano', 'Harpo': 'harpo'} 
    print(marx_list[2])          # harpo
    print(marx_tuple[2])         # harpo
    print(marx_dict['Harpo'])    # harpo


容器中可以包含不同类型的元素，也可以包含其他的容器物件::

    dict_of_lists = {'Stooges': ['Moe', 'Curly', 'Larry'],
                    'Marxes': ['Groucho', 'Chico', 'Harpo'],
                    'Pythons': ['Chapman', 'Cleese', 'Gilliam', 'Jones', 'Palin']}
    print(dict_of_lists)
    print(dict_of_lists['Marxes'])      # ['Groucho', 'Chico', 'Harpo']
    print(dict_of_lists['Marxes'][1])   # Chico







