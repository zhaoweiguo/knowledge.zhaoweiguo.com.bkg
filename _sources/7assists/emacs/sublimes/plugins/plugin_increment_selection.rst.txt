Increment Selection
###################

Increment Selection 介绍
在 Sublime Text 中为每个选择添加一个数字，每个选择增加一次。

默认的快捷键是::

    ctrl alt i or cmd ctrl i.


插件地址: https://packagecontrol.io/packages/Increment%20Selection

Examples
========

Tips: [] stands for a selection, | stands for a caret::

    [1] text [1] text [1] -> 1| text 2| text 3|
    [a] text [a] text [a] -> a| text b| text c|
    [A] text [A] text [A] -> A| text B| text C|
    [01] text [01] text [01] -> 01| text 02| text 03|
    [05,2] text [05,2] text [05,2] -> 05| text 07| text 09|
    [5,-1] text [5,-1] text [5,-1] -> 5| text 4| text 3|
    [a,3] text [a,3] text [a,3] -> a| text d| text g|
    
Increment follows the difference between the first and second element::

    [10] text [9] text [1] -> 10| text 9| text 8|   
    [a] text [c] text [a] -> a| text c| text e|

Generate line numbers::

    [#] line -> 1| line
    [#] line -> 2| line
    [#] line -> 3| line
    [#] line -> 4| line
    [#] line -> 5| line








