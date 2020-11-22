表相关
############


表的使用::

    // 特殊表名使用
    db.getCollection("3 test").find()
    db.getCollection("3-test").find()
    db.getCollection("stats").find()

    //To format the printed result, you can add the.pretty() 
    db.myCollection.find().pretty()

    print()
    print(tojson(<obj>)) 
    printjson()


删除表(集合)::

    db.collection.drop()





