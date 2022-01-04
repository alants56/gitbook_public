# MongoDB Guide



### 1.启动

```sh
# 服务启动
./mongod --dbpath ../data

# 连接数据库
./mongo
```



### 2. 创建数据库

```sh
use guide
```

如果guide不存在，则创建数据库；否则切换到制定数据库。



### 3.查看数据库

```sh
db
```

查看所有的数据库（磁盘）

```sh
show databases
show dbs
```

注意：刚创建的没有数据的数据库只会存在内存中，不会存储在磁盘。

