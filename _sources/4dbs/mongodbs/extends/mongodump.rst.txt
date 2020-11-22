mongodump数据导入导出
=============================
::

    mongodump -u<user> -p<pwd> -h<host>:<port> -d <dbname> -o <path.bson>   # 导出

    mongorestore -u<user> -p<pwd> -h<host>:<port> --directoryperdb <path.bson>  # 把<path.bson>数据导入mongo

