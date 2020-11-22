Web Server
################

node版::

    // http server软件
    npm install -g http-server
    // 使用
    http-server &


python版::

    python -m SimpleHTTPServer 8888 &

    如果是Python 3+
    python -m http.server 8888 &

shell版::

    nc命令

golang版::

    $ go get -u github.com/shurcooL/goexec

    $ goexec 'http.ListenAndServe(`:8080`,http.FileServer(http.Dir(`.`)))'








