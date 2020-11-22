json_pp命令
###########

功能::

    格式化json

示例::

    $ echo '{"result":[{"addr":"32hxx","txids":["bef80ffd"]}],"error":null,"id":"test"}' | json_pp
    {
       "error" : null,
       "id" : "test",
       "result" : [
          {
             "addr" : "32hxx",
             "txids" : [
                "bef80ffd"
             ]
          }
       ]
    }




