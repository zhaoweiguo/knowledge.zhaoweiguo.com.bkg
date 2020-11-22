iterm2相关
###################

技巧1:有跳板机的服务器上「上传」「下载」文件
'''''''''''''''''''''''''''''''''''''''''''''''''

1. 下载 rz,sz命令
2. 首先进入:

.. figure:: /images/emacs/iterm2_pic2.png
   :width: 80%

3. 然后进入:

.. figure:: /images/emacs/iterm2_pic3.png
   :width: 80%

4. 可参考开源项目 [1]_ 下载2个sh文件
5. 注意::

    a.两个sh文件必须放在/usr/local/bin目录下,且可运行
    b.rz,sz命令都要放到/usr/local/bin目录下
    c.不可在screen,tmux等下使用


技巧2:与tmux配合,把上传复制的文件转到「剪切板」上
'''''''''''''''''''''''''''''''''''''''''''''''''
.. figure:: /images/emacs/iterm2_pic1.png
   :width: 80%

技巧3:高亮当前行
''''''''''''''''
.. figure:: /images/emacs/iterm2_pic4.png
   :width: 80%




.. [1] https://github.com/mmastrac/iterm2-zmodem



