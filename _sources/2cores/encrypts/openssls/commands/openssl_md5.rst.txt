openssl md5命令
###############

MD5对文件或字符串加密::

    $ cat filename.txt 
    zhaohang

    $ openssl md5 filename.txt 
    MD5(filename.txt)= c47df1e95ae452e959fcc73cda1a3e77

    $ echo "zhaohang" |openssl dgst -md5
    c47df1e95ae452e959fcc73cda1a3e77

    $ md5sum filename.txt 
    c47df1e95ae452e959fcc73cda1a3e77 filename.txt




