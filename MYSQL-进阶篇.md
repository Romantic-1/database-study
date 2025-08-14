# 1.存储引擎

## 1.1 mysql体系结构

### 1.连接层

主要接收客户端的连接，完成一些连接的处理，以及认证授权的相关操作，以及相关的一些安全方案，还有去检查是否超过最大连接数等等

比如输入用户名密码就是在连接层进行校验的（授权认证）并且校验客户端的权限

### 2.服务层

绝大部分的核心功能都是在服务层完成的，比如SQL接口，查询解析器，查询解析器，查询缓存

跨存储引擎的实现，也都是在服务层实现的

DML，DDL，视图，存储过程，触发器

### 3. 存储引擎层

mysql提供了很多的存储引擎给我们选择 ，如果这些存储引擎不满足我们的需求，我们还可以在其基础上进行扩展（所以称为：可插拔式存储引擎）

它控制的就是mysql当中的数据的存储和提取的方式

 注意：index 索引是在存储引擎层实现的，（不同的存储引擎，索引的结构是不一样的）

### 4.存储层

具体数据库的数据是存储磁盘当中的

包含：一系列的日志，redo.log    undo.log   data数据   index索引   二进制   错误日志  查询日志   慢查询日志

![image-20250813224912248](https://raw.githubusercontent.com/Romantic-1/ImgBed/main/20250813224912377.png)



## 1.2 存储引擎简介

不同的引擎有不同的应用场景

存储引擎就是存储数据、建立索引、更新/查询数据等技术的实现方式。<span style="color:#FF3333;">存储引擎是基于表的，而不是基于库的，所以存储引擎也可被称为表类型</span>。



建表的时候没有指定存储引擎，会有一个默认的存储引擎 InnoDB 

--- 查看建表语句

![image-20250813230447854](https://raw.githubusercontent.com/Romantic-1/ImgBed/main/20250813230447957.png)

engine 存储引擎

auto_increment 表示id是自增的   auto_increment=5 表示下一条新增的数据id为5

default  charset 当前表的字符集默认是utf8mb4 

collate 排序方式。为utf8mb4_0900_ai_ci

comment 注释信息



### 1.在创建表时，指定存储引擎

关键字：engine   引擎

![image-20250813231006229](https://raw.githubusercontent.com/Romantic-1/ImgBed/main/20250813231006323.png)

### 2.查看当前数据库支持的存储引擎

```sql
show engines;
```

![image-20250813231525222](https://raw.githubusercontent.com/Romantic-1/ImgBed/main/20250813231525354.png)

### 3.创建表的时候指定存储引擎

```sql
创建表my_myisam，并指定MyISAM存储引擎
create table my_myisam(
   id int,
   name vachar(10)
)engine=MYISAM;


创建表my_memory，指定Memory存储引擎
create table my_myisam(
   id int,
   name vachar(10)
)engine=memory;
```







## 1.3 存储引擎特点

InnoDB

InnoDB是一种兼顾高靠性和高性能的通用存储引擎，在MySQL5.5之后，InnoDB是默认的MySQL存储引擎。



事务，外键，行级锁



**1.DML操作遵循ACID模型，支持事务；**

**2.行级锁，提高并发访问性能；**

**3.支持外键FOREIGNKEY约束，保证数据的完整性和正确性；**





## 1.4 存储引擎的特点



















# 2.索引

# 3.SQL优化

# 4.识图/存储过程/触发器

# 5.锁

# 6.Inno DB引擎

# 7.MYSQL管理