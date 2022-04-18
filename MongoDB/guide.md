# MongoDB Guide



| MongoDB     | SQL         |
| ----------- | ----------- |
| database    | database    |
| collection  | table       |
| document    | row         |
| filed       | column      |
| index       | index       |
| primary key | primary key |





### 1.启动

```sh
# 服务启动
./mongod --dbpath ../data

# 连接数据库
./mongo
```

### 2. 数据库

1. 创建数据库

```sh
use guide
```

如果guide不存在，则创建数据库；否则切换到制定数据库。

 2.查看数据库

查看所有的数据库（磁盘）

```sh
show databases
show dbs
```

注意：刚创建的没有数据的数据库只会存在内存中，不会存储在磁盘。

查看当前数据库

```
db
```

 3.删除数据库

```
db.dropDataBase()
```

## 3.集合

1.创建集合

* 显示创建

```
db.createCollection("demo")
```

* 隐式创建

```
db.demo.insert({"name":"guide"})
```



2.查询

```
show collections
```

3.删除

```
db.demo.drop()
```



### 4.文档

1. 插入

```
db.demo.insert({"name":"guide"})
db.demo.insertMany([{"name":"guide1"},{"name":"guide2"}])
```

使用try catch捕获插入异常

```
try {
	db.demo.insertMany([{"name":"guide1"},{"name":"guide2"}])
} catch(e) {
	print(e)
}
```



2.查询

```
//查询所有
db.demo.find()

//条件查询
db.demo.find({"name":"guide"})
db.demo.find({"name":"guide"},{_id:0})
//查询一条数据
db.demo.findOne()
```



3.更新

覆盖修改

```
db.demo.update({_id:"1"},{likenum:NumberInt(1001)})
```

局部修改

```
db.demo.update({_id:"1"},{$set:{likenum:NumberInt(1001)}})
db.demo.update({_id:"1"},{$inc:{likenum:NumberInt(1)}})
```

批量修改

 ```
 db.demo.update({_id:"1"},{$set:{likenum:NumberInt(1001)}},{multi:true})
 ```



4.删除

```
db.demo.remove({})
```



### 5.查询

```
//数量查询
db.demo.count()

//分页查询
db.demo.find().limit(2)
db.demo.find().limit(2).skip(2)

//排序查询
db.demo.find().sort({name:1})
```



正则查询

```
db.demo.find({name:/regStr/})
```



比较查询:\$gt, \$lt, \$gte, \$lte, \$ne

```
db.demo.find({name:( $gt: value)})
```



包含查询：\$in，不包含 、$nin

```
db.demo.find({name: {$in:["guide","guide1"]}})
```



条件查询：\$and和\$or 

```
db.demo.find({$and:[{name:guide},{likenum:{$lt:NumberInt(2)}}]})
```



### 6.索引

创建

```
db.demo.createIndex(keys,options)
db.demo.createIndex({name:1})
```



查询

 ```
 db.demo.getIndexes()
 ```



移除

```
db.demo.dropIndex({name:1})
db.demo.dropIndexs()
```

