# 1.当前主流的关系型数据库

Oracle

Mysql

SQL server

PostgreSQL

IBM db2



# 2.MySQL的安装及启动

## 2.1 mysql的版本

### 2.1.1 社区版

免费，mysql不提供技术支持

### 2.1.2 商业版

收费，官方提供技术支持



## 2.2 mysql的下载

下载地址：[MySQL :: Download MySQL Community Server (Archived Versions)](https://downloads.mysql.com/archives/community/)

![image-20250723224611358](https://raw.githubusercontent.com/Romantic-1/ImgBed/main/20250723224611463.png)

Windows的安装步骤：

1.双击安装包，运行

2.选择开发者模式安装

![image-20250723224623913](https://raw.githubusercontent.com/Romantic-1/ImgBed/main/20250723224624064.png)

3.下面是罗列mysql安装的所有组件，直接执行就好了

![image-20250723224635376](https://raw.githubusercontent.com/Romantic-1/ImgBed/main/20250723224635548.png)

4.安装完成之后，进入了配置界面

mysql默认端口3306

![image-20250723224648393](https://raw.githubusercontent.com/Romantic-1/ImgBed/main/20250723224648561.png)

5.接着使用推荐的安装

![image-20250723224659543](https://raw.githubusercontent.com/Romantic-1/ImgBed/main/20250723224659732.png)

6.账户及角色的设置页面

![image-20250723224709768](https://raw.githubusercontent.com/Romantic-1/ImgBed/main/20250723224709917.png)

7.自动帮windows注册一个mysql的服务，并且开机自启

![image-20250723224720516](https://raw.githubusercontent.com/Romantic-1/ImgBed/main/20250723224720629.png)

## 2.3 mysql的启动与停止

直接命令行中输入

``` bash 
net start mysql80
net stop mysql80
```



## 2.4 mysql 的连接

1. 命令行工具连接

   ``` bash
   mysql -h 127.0.0.1 -P 3306 -uroot -p
   输入密码
   ```

   注意：要想在任意的目录下连接mysql，需要配置全局的环境变量

   在系统的环境编辑PATH，新增一条mysql的bin目录的配置

   ![image-20250723224742018](https://raw.githubusercontent.com/Romantic-1/ImgBed/main/20250723224742168.png)



## 2.5 mysql的数据模型

![image-20250723224751589](https://raw.githubusercontent.com/Romantic-1/ImgBed/main/20250723224751696.png)

### 2.5.1 关系型数据库

概念：建立在关系模型基础上，由多张互相连接的二维表组成的数据库

二维表：

![image-20250723224802574](https://raw.githubusercontent.com/Romantic-1/ImgBed/main/20250723224802735.png)

特点：

使用表结构存储数据，格式统一，便于维护

使用sql语言来进行操作，标准统一，使用方便







# 3.SQL的讲解

## 3.1 SQL的通用语法

SQL语句可以单行或多行书写，以分号结尾。

SQL语句可以使用空格/缩进来增强语句的可读性。

MySQL数据库的SQL语句不区分大小写，关键字建议使用大写。

注释：
	单行注释：--  注释内容     或     #注释内容（MySQL特有）
	多行注释：/*  注释内容  */

## 3.2 SQL的分类

### 3.2.1 DDL

数据定义语言，用来定义数据库对象（数据库，表，字段）

### 3.2.2 DML

数据操作语言，用来对数据库表中的数据，进行增删改操作

### 3.2.3 DQL

数据库查询语言，用来查询数据库中表的数据

### 3.2.4 DCL

数据控制语言，用来创建用户，控制数据库的访问权限





## 3.3 DDL

### DDL -数据库操作-查询，创建，删除，使用



``` sql
查询所有数据库
SHOW DATABASES;

查询当前数据库
SELECT DATABASE();

创建数据库
CREATE DATABASE [ IF NOT EXISTS] 数据库名 [ DEFAULT CHARSET 字符集 ] [COLLATE 排序规则];

删除数据库
DROP DATABASE [IF EXISTS] 数据库名;

使用数据库
USE 数据库名;

```

![image-20250723224819742](https://raw.githubusercontent.com/Romantic-1/ImgBed/main/20250723224819897.png)

![image-20250723224835788](https://raw.githubusercontent.com/Romantic-1/ImgBed/main/20250723224835933.png)

如果不存在则创建数据库，存在则不创建，不会报错

```sql
CREATE DATABASE IF NOT EXISTS 数据库名
```



![image-20250723224848360](https://raw.githubusercontent.com/Romantic-1/ImgBed/main/20250723224848451.png)

设置utf8mb4字符集

```sq
CREATE DATABASE  IF NOT EXISTS 数据库名  DEFAULT CHARSET 字符集 
```

![image-20250723224901707](https://raw.githubusercontent.com/Romantic-1/ImgBed/main/20250723224901853.png)

删除数据库
``` sql
DROP DATABASE [IF EXISTS] 数据库名;
```

[IF EXISTS] 如果存在则删除，不存在则不删除，这样就不会报错了

![image-20250723224918402](https://raw.githubusercontent.com/Romantic-1/ImgBed/main/20250723224918543.png)

使用数据库

```sql
USE 数据库名;
```





### DDL-表结构-查询

``` sql
查询当前数据库的所有表
SHOW TABLES;
```



``` sql
查询表结构
DESC 表名;
```



```sql
查询指定表的建表语句
SHOW CREATE TABLE 表名;
```



### DDL-表操作-创建

<b>注意：[..]为可选参数，最后一个字段后面没有逗号</b>

``` sql
创建表
CREATE TABLE 表名(
   字段1 字段1类型 [COMMENT 字段1注释],
   字段2 字段2类型 [COMMENT 字段2注释],
   字段3 字段3类型 [COMMENT 字段3注释],
   ........
   字段n 字段n类型 [COMMENT 字段n注释]
)[COMMENT 表注释];

```

![](https://raw.githubusercontent.com/Romantic-1/ImgBed/main/20250723224925670.png)

注意：在命令行界面中，没有敲分号，回车是继续写的

验证数据库是否创建完毕

```sql
SHOW TABLES
```

![image-20250723211414277](https://raw.githubusercontent.com/Romantic-1/ImgBed/main/20250723224931863.png)

查看数据库表的结构

```sql
desc 表名
```

![image-20250723211933717](https://raw.githubusercontent.com/Romantic-1/ImgBed/main/20250723211936632.png)

查看表的创建的sql语句

```sql
SHOW create table 表名
```

![image-20250723212117704](https://raw.githubusercontent.com/Romantic-1/ImgBed/main/20250723212117843.png)

但是查看表创建语句时候，有一部分，我们并没有编写的

![																																																																																																																																													](https://raw.githubusercontent.com/Romantic-1/ImgBed/main/20250723212357556.png)

engine 存储引擎 = InnoDB

default charset 默认字符集 = utf8mb4

collate 排序规则 = utf8mb4_0900_ai_ci



### DDL-表操作-数据类型

主要分为3类

数值类型，字符串类型，日期时间类型



#### 1.数值类型

![image-20250723215220714](https://raw.githubusercontent.com/Romantic-1/ImgBed/main/20250723215220865.png)

| 分类 | 类型        | 大小  | （sigend）有符合范围 | （unsigend）无符号范围 | 描述                 |
| ---- | ----------- | ----- | -------------------- | ---------------------- | -------------------- |
|      | tinyInt     | 1字节 |                      |                        | 小整数值             |
|      | smallInt    | 2字节 |                      |                        | 大整数值             |
|      | meduiInt    | 3字节 |                      |                        | 大整数值             |
|      | INT/INTEGRE | 4字节 |                      |                        | 大整数值             |
|      | BigInt      | 8字节 |                      |                        | 极大整数值           |
|      | float       | 4字节 |                      |                        | 单精度浮点数值       |
|      | double      | 8字节 |                      |                        | 双精度浮点数值       |
|      | decimal     |       |                      |                        | 小数值（精确定点数） |

精度：表示整个数值的长度，比如123.45的精度就是5

标度：表示小数位数，比如123.45的标度就是2



案例：

​	在表中描述用户的年龄，age  用int   我们选择 tinyInt  然后选择无符号范围（unsigend）

​	结果： age tinyInt unsigend

​	分数：使用double（4，1）  4代表整体长度，1代表小数的位数



#### 2.字符串类型

![image-20250723220332769](https://raw.githubusercontent.com/Romantic-1/ImgBed/main/20250723220332912.png)



char 和 varchar，我们后面都会跟上一个参数

char(10),varchar(100)

表示当前字符串能够存储的最大长处是多少，只能存储10个字符



什么是定长，什么是变长：

定长字符串，char(10)，如果只是存储了一个字符的空间，但是他还是会占用10个字符的空间，未占用的字符，其他空间会用空格进行补位

变长：则会根据存储在字符串来进行占用空间



char 和 varchar 的差异：

char 的性能更高，因为varchar，我们在使用的时候，它需要根据内容来计算它所占用的空间

char不需要计算空间，因此性能好，空间差，

varchar需要计算空间，因此性能差，空间好



确定的就使用char，不确定的就使用varchar

![image-20250723221622911](https://raw.githubusercontent.com/Romantic-1/ImgBed/main/20250723221623038.png)





#### 3.日期时间类型

![image-20250723221642161](https://raw.githubusercontent.com/Romantic-1/ImgBed/main/20250723221642313.png)

描述某个同事的生日，用DATE更好



#### 5.案例

![image-20250723221848138](https://raw.githubusercontent.com/Romantic-1/ImgBed/main/20250723221848283.png)

```sql
create table workers_info(
   id int comment "员工编号",
   number varchar(10) comment "员工工号",
   name varchar(10) comment "员工姓名",
   gender char(1) comment "性别",
   age tinyInt unsigned comment "年龄",
   idcard char(18) comment "身份证号",
   time date comment "入职时间"
) comment "员工信息表";
```

![image-20250723222628336](https://raw.githubusercontent.com/Romantic-1/ImgBed/main/20250723222628440.png)



### DDL-表操作-修改

##### 1.添加字段

```sql
alter table 表名 add 字段名 数据类型（长度） comment “注释” 约束;
```

为emp表增加一个新的字段”昵称”为nickname，类型为varchar(20)

![image-20250723223043367](https://raw.githubusercontent.com/Romantic-1/ImgBed/main/20250723223043517.png)

##### 2.修改字段

​	修改数据类型

```sql
alter table 表名 modify 字段名 新数据类型（长度）;
```

​	修改字段名和字段类型

```sql
alter table 表名 change 旧字段名 新字段名 数据类型（长度） comment “注释“ 约束 ;
```

将emp表的nickname字段修改为username，类型为varchar(30)

![image-20250723223533591](https://raw.githubusercontent.com/Romantic-1/ImgBed/main/20250723223533760.png)

##### 3.删除字段

```sql
alter table 表名 drop 字段名
```

案例:
将emp表的字段username删除

![image-20250723223647819](https://raw.githubusercontent.com/Romantic-1/ImgBed/main/20250723223647975.png)

##### 4.修改表名

```sql
alter table 表名 rename to 新表名
```

案例：
将emp表的表名修改为employee

![image-20250723223824279](https://raw.githubusercontent.com/Romantic-1/ImgBed/main/20250723223824390.png)

##### 5.删除表

删除指定的表，并且判断是否存在再删除

```sql
drop table [if exists] 表名;
```

![image-20250723224055411](https://raw.githubusercontent.com/Romantic-1/ImgBed/main/20250723224055576.png)

删除指定表，并重新创建该表（意思就是删除表数据，但是不删除表结构）

```sql
truncate table 表名;
```

![image-20250723224207914](https://raw.githubusercontent.com/Romantic-1/ImgBed/main/20250723224208057.png)





## 3.4 DML

DML用来对数据库中表的数据记录进行增删改操作。

添加数据，修改数据，删除数据

#### DML-添加数据

注意：
插入数据时，指定的字段顺序需要与值的顺序是一一对应的，如果是全部字段插入数据，应该是一一对应的。
字符串和日期型数据应该包含在引号中。
插入的数据大小，应该在字段的规定范围内。

##### 1.给指定字段添加数据

```sql
insert into 
表名（字段名1，字段名2，....）
values（值1，值2，.........）
```



##### 2.给全部字段添加数据

```sql
insert into 表名
values(值1，值2，.........)
```



##### 3.批量添加指定字段的值

```sql
insert into 
表名（字段名1，字段名2，....）
values（值1，值2，.........）,   注意：多个数据用逗号区别
		 （值1，值2，.........）,
		  （值1，值2，.........）
; 
```

##### 4.批量给全部字段赋值

```sql
insert into 表名
values(值1，值2，.........),   注意：多个数据用逗号区别
		(值1，值2，.........),
		(值1，值2，.........)
;
```





##### 5.例子

插入一条数据

![image-20250726162525582](https://raw.githubusercontent.com/Romantic-1/ImgBed/main/20250726162525789.png)

age 设定是tinyint unsigned 字段，插入负数是会报错的

![image-20250726162738909](https://raw.githubusercontent.com/Romantic-1/ImgBed/main/20250726162739124.png)

插入全部字段

![image-20250726162919141](https://raw.githubusercontent.com/Romantic-1/ImgBed/main/20250726162919343.png)

添加多条数据，多条数据使用逗号分离

![image-20250726163312089](https://raw.githubusercontent.com/Romantic-1/ImgBed/main/20250726163312302.png)





#### DML-修改数据

 ```sql
 update 表名
 set 字段名1=值1,
 	 字段名2=值2，
 	 .....
 where 条件
 ;
 ```

注意：修改语句的条件可以有，也可以没有，如果没有条件，则会修改整张表的所有数据。





##### 案例：

修改id为1的数据，将name修改为itheima

 ```sql
 update employee
 set name = "itheima"
 where id = 1;
 ```



修改id为1 的数据，将name修改为小昭，gender修改为女

```sql
update employee
set name = "itheima",
	 gender = "女"
where id = 1;
```

将所有的员工入职日期修改为2008-01-01 (没有条件，则会修改整张表的所有数据)

```sql
update employee
set entrydate = "2008-01-01";
```





#### DML删除数据

```sql
delete from 表名 [where 条件]
```

注意：
delete语句的条件可以有，也可以没有，如果没有条件，则会删除整张表的所有数据。

delete语句不能删除某一个字段的值(可以使用UPDATE)。



##### 案例

删除所有gender为女的数据

```sql
delete from employee
where gender = "女人"
```

删除所有员工

delete from employee





## 3.5 DQL

DQL是用来查询数据的，select

group by 分组字段列表

having  分组后条件列表

order by 排序字段列表

limit  分页查询





基本查询

条件查询，where

聚合函数，count，max，min，avg，sum

分组查询，group by

排序查询，order by

分页查询，limit



### DQL-基本查询

#### 1.查询多个字段

```bash
select 字段1，字段2，....
from
	表名
```

![image-20250729221232830](https://raw.githubusercontent.com/Romantic-1/ImgBed/main/20250729221250827.png)

查询这个表的所有字段

```sql
select * from 表名
```

![image-20250729221320893](https://raw.githubusercontent.com/Romantic-1/ImgBed/main/20250729221321056.png)



#### 2.设置别名

```sql
select 字段1 as 别名,
		 字段2 as 别名,
		  .....
from 表名
```

![image-20250729221343395](https://raw.githubusercontent.com/Romantic-1/ImgBed/main/20250729221343558.png)

注意 as 是可以省略的



#### 3.去除重复记录（distinct）

关键字 distinct

```sql
select distinct  字段
from 表名
```

![image-20250729221447061](https://raw.githubusercontent.com/Romantic-1/ImgBed/main/20250729221447247.png)







### DQL-条件查询

#### 1.语法

```sql
select 字段列表 from 表名 where 条件列表;
```

条件列表可以分为比较运算符和逻辑运算符

![image-20250729221718235](https://raw.githubusercontent.com/Romantic-1/ImgBed/main/20250729221718376.png)

between.....and..... 在某个范围之内

in(.......) 在in里面的数值

like 模糊匹配       _匹配单个字符，%匹配任意个字符

#### 2.11个案例

```sql
条件查询
1.查询年龄等于88的员工
select * from emp where age = 88;
2.查询年龄小于20的员工信息
select * from emp where age < 20;
3.查询年龄小于等于20的员工信息
seletc * from emp where age <= 20;
4.查询没有身份证好的员工信息
select * from emp where idcard is NULL;
5.查询有身份证号的员工信息
select * from emp where idcard is not NULL;
6.查询年龄不等于88的员工信息
select * from emp where age != 88;
7.查询年龄在15岁（包含）到20岁（包含）之间的员工信息
select * from emp where age between 15 and 20
select * from emp where age >= 15 and age <= 20
8.查询性别为女且年龄小于25岁的员工信息
select * from emp where gender = "女" and age < 25;
9.查询年龄等于18或20或40的员工信息
select * from emp where age = 18 or age = 20 or age = 40
select * from emp where age in (18,20,40)
10.查询姓名为两个字的员工信息
select * from emp where name like "__"
11.查询身份证号最后一位是X的员工信息
select * from emp where name like "%X"
```







### DQL-聚合函数

#### 1.聚合函数

count 统计数量                max 求最大值             min 求最小值             avg 求最小值                sum 求和

作用于表当中的某一列



注意：

使用聚合函数的时候，所有的NULL值是不参与聚合函数运算的





#### 2.语法

```bash
select 聚合函数(字段列表) from 表名;
```

#### 3.案例

```sql
1.统计该企业员工数量
select count(*)  from emp;
select count(id) from emp;
 
2.统计该企业员工的平均年龄
select avg(age) from emp;

3.统计该企业员工的最大年龄
select max(age) from emp;

4.统计该企业员工的最小年龄
select min(age) from emp;

5.统计西安地区员工的年龄之和
select sum(age) from emp where workaddress = "西安";
```



### DQL-分组查询

#### 1.关键字 group by



注意

执行顺序:        where       >    聚合函数        >        having 
分组之后，查询的字段一般为聚合函数和分组字段，查询其他字段无任何意义。



#### 2.语法

```sql
select 字段列表
from 表名
where 条件列表
group by 分组字段名
having 分组后的过滤条件;
```



#### 3.where和having的区别

1.执行的时机不同

where 是分组之前进行过滤的，如果不满足where的条件，则不参与分组

having是分组之后对结果进行过滤

2.判断的条件不同

where不能对聚合函数进行判断，having可以



#### 4.案例

```sql
分组查询
1.根据性别分组，统计男性员工和女性员工的数量
select gender,count(*) from emp group by gender;

2.根据性别分组，统计男性员工和女性员工的平均年龄
select gender,avg(age) from emp group by gender;

3。查询年龄小于45的员工，并根据工作地址分组，获取员工数量大于等于3的工作地址
select workaddress,count(*)
from emp
where age < 45
group by workaddress
having count(*) >= 3;

起个别名：
select workaddress,address_count
from emp
where age < 45
group by workaddress
having address_count >= 3;


```

![image-20250729230028341](https://raw.githubusercontent.com/Romantic-1/ImgBed/main/20250729230028558.png)

![image-20250729230119856](https://raw.githubusercontent.com/Romantic-1/ImgBed/main/20250729230120065.png)

![image-20250729230326275](https://raw.githubusercontent.com/Romantic-1/ImgBed/main/20250729230326490.png)









### DQL-排序查询

order by  支持多字段排序

#### 1.基本语法

```sql
select 字段列表
from 表名
order by 字段1 排序方式1
order by 字段2 排序方式2;
```



#### 2.排序方式

ASC：升序

desc：降序

如果是多字段排序，当第一个字段值相同时，才会根据第二个字段进行排序。



#### 3.案例

```sql
排序查询
1.根据年龄对公司的员工进行升序排序
select * from emp 
order by age asc;


2.根据入职时间，对员工进行降序排序
select * from emp 
order by age entrydate desc;

3.根据年龄对公司的员工进行升序排序，年龄相同，再按照入职时间进行降序排序
select * from emp
order by age asc,
order by entrydate desc;
```







### DQL-分页查询

#### 1.基本语法

```sql
select * from emp limit 起始索引，查询记录数;
```

#### 2.分页查询的注意

![image-20250730224058734](https://raw.githubusercontent.com/Romantic-1/ImgBed/main/20250730224058955.png)

#### 3.案例

```sql
分页查询
1.查询第1页员工数据，每页展示10条记录
select * from emp limit 10;
select * from emp limit 0,10;


2.查询第2页员工数据，每页展示10条记录
select * from emp limit 10,10;

```





### DQL语句查询编写

```sql
1.查询年龄为20,21,22,23岁的员工信息。
select * from emp where age in (21,21,22,23);

2.查询性别为男，并且年龄在20-40岁（含)以内的姓名为三个字的员工。
select * from emp where gender = "男" and age between 12 and 40 and name like "___";

3.统计员工表中，年龄小于60岁的，男性员工和女性员工的人数。
select gender,count(*) from emp where age<60 group by gender;

4.查询所有年龄小于等于35岁员工的姓名和年龄，并对查询结果按年龄升序排序，如果年龄相同按入职时间降序排序。
select name,age from emp where age <=35 
order by age asc,
order by entrydate desc;


5.查询性别为男，且年龄在20-40岁（含）以内的前5个员工信息，对查询的结果按年龄升序排序，年龄相同按入职时间升序排序。

select * from emp where age between 20 and 40
order by age asc,
order by entrydate desc
limit 0,5;
```

### DQL执行顺序

编写顺序与执行顺序不一样

![image-20250731225230748](https://raw.githubusercontent.com/Romantic-1/ImgBed/main/20250731225230965.png)

验证dql语句的执行顺序

查询年龄大于15的员工的姓名、年龄，并根据年龄进行升序排序
select name,age from emp where age >15 order by age asc;





### DQL小结

![image-20250731225731616](https://raw.githubusercontent.com/Romantic-1/ImgBed/main/20250731225731820.png)





## 3.6 DCL语句

DCL英文全称是DataControlLanguage(数据控制语言)，用来管理数据库用户、控制数据库的访问权限。



限制哪些用户可以访问mysql服务器

当用户访问mysql，他能操作哪几个数据库



### 1. DCL-管理用户

#### 查询用户

所有存放数据库用户的信息，都是存放在mysql这个数据库中

```sql
use mysql; 
select * from user;
```

默认mysql有四个用户

注意：需要用户名和主机地址（Host 和 User），两个双重条件才能定位一个用户数据

localhost，代表只能本机访问，不能远程访问

任意主机可以访问数据库，用通配符%



注意：
主机名可以使用%通配。
这类SQL开发人员操作的比较少，主要是DBA（DatabaseAdministrator数据库管理员）使用。



![image-20250731230147472](https://raw.githubusercontent.com/Romantic-1/ImgBed/main/20250731230147619.png)



#### 创建用户

```sql
create user "用户名"@"主机名" identified by "密码"

创建用户 itcast，只能够在当前主机LocaLhost访问，密码123456；

create user "itcast"@"localhost" identified by "123456"

创建用户heima可以在任意主机访问该数据库，密码123456
create user "heima"@"%" identified by "123456"
```





#### 修改用户密码

```sql
alert user "用户名"@"主机名" identified with mysql_native_password by "新密码"

修改用户heima的访问密码为1234；
alert user "heima"@"%" identified with mysql_native_password by "1234"

```





#### 删除用户

```sql
drop user "用户名"@"主机名"

删除itcast@localhost用户
drop user "itcast"@"localhost"
```



### 2.DCL-权限控制

用户创建好之后需要给它分配权限

**注意：**
·多个权限之间，使用逗号分隔
授权时，数据库名和表名可以使用＊进行通配，代表所有。

#### 常用权限：

ALL、ALL privileges     所有权限

select                            查询权限 

insert                            插入数据

update                         更新数据

delete                         删除数据

alter                           修改表

drop                            删除数据库/表/识图

create                          创建数据库/表

usage                           只能登陆上来，没有权限

![image-20250803102554859](https://raw.githubusercontent.com/Romantic-1/ImgBed/main/20250803102555046.png)

#### 查询权限

```sql
SHOW grants for "用户名"@"主机名"
```

查询heima用户的权限

![image-20250803103427699](https://raw.githubusercontent.com/Romantic-1/ImgBed/main/20250803103427877.png)







#### 赋予权限

```sql
grant 权限列表 on 数据库名.表名 to ”用户名“@"主机名"
```

所有数据库所有表，使用          *.*

给heima用户的itcast库的所有表，授予所有权限：

```sql
grant all on itcast.* to 'heima'@'%';
```



![image-20250803103604424](https://raw.githubusercontent.com/Romantic-1/ImgBed/main/20250803103604549.png)







#### 撤销权限

```sql
revork 权限列表 on 数据库名.表名 from ”用户名“@"主机名"
```

撤销heima用户下所有权限，itcast数据库下所有的表

```sql
revoke all on itcast.* from 'heima'@'%”
```

再查看权限就变回只有usage了



## 3.7 函数

### mysql函数

函数是指一段可以直接被另一段程序调用的程序或代码。

mysql里面是内置函数了，我们只是调用就好了

![image-20250803104753775](https://raw.githubusercontent.com/Romantic-1/ImgBed/main/20250803104753989.png)





### 1.字符串函数

#### 常用的字符串函数

| concat(s1,s2,s3.......sn) | 字符串拼接，将s1,s2........sn拼接为一个字符串                |
| ------------------------- | ------------------------------------------------------------ |
| lower(str)                | 将字符串str全部转为小写                                      |
| upper(str)                | 将字符串str全部转为大写                                      |
| lpad(str,n,pad)           | 左填充，用字符串pad对str的左边进行填充，达到n个字符串长度    |
| rpad(str,n,pad)           | 右填充，用字符串pad对str的右边进行填充，达到n个字符串长度    |
| trim(str)                 | 去掉字符串头部和尾部的空格                                   |
| substring(str,start,len)  | 返回从字符串str从start位置起的len个长度的字符串，注意，索引是从1开始的 |

#### 案例

##### 1.concat字符串拼接

```sql
select concat("hello","mysql");
```

##### 2.lower大写转换为小写

```sql
select lower('Hello'）;
```

##### 3.upper小写转换为大写

```sql
select upper（'Hello');
```

##### 4.lpad左边指定位数填充字符串

```sql
select lpad('01'，5,'-');
```

![image-20250803110203337](https://raw.githubusercontent.com/Romantic-1/ImgBed/main/20250803110203535.png)

##### 5.rpad右边指定位数填充字符串

```sql
select lpad('01'，5,'-');
```

![image-20250803110239228](https://raw.githubusercontent.com/Romantic-1/ImgBed/main/20250803110239369.png)

##### 6.trim去除前后空格

```sql
select trim(' Hello MySQL  '）；
```



##### 7.substring截取字符串

注意：索引是从1开始截取的

```sql
select substring("hello mysq",1,5)
```

![image-20250803110539595](https://raw.githubusercontent.com/Romantic-1/ImgBed/main/20250803110539799.png)

##### 8.具体案例：

由于业务需求变更，企业员工的工号，统一为5位数，目前不足5位数的全部在前面补0。比如：1号员工的工号应该为00001

```sql
update emp 
set worknumber = lpad(worknumber,5,"0");
```

这里需要注意的是如果你的worknumber定义类型不是char类型，那么这行操作是无效的












### 2.数值函数

---

#### 常见的数值函数

| ceil(x)    | 向上取整                             |
| ---------- | ------------------------------------ |
| floor(x)   | 向下取整                             |
| mod(x,y)   | 返回x/y的模                          |
| rand()     | 返回0~1内的随机数                    |
| round(x,y) | 求参数x，的四舍五入的值，保留y位小数 |



##### 1.ceil函数-向上取整

只要小数位不是0，都是2

```sql
select ceil(1.5)

输出为2
1.1也是2
```



##### 2.floor函数-向下取整

只要小数位不是0，都是1

```sql
select ceil(1.9)

输出为1
1.1也是1
```

##### 3.mod函数，取余数

```sql
select mod(7,4)

输出为3.7 除于4的余数为3
```

#####4.rand 随机数

返回0~1内的随机数

```sql
select rand()
```

##### 5.round四舍五入

```sql
select round(2.34,2)

输出2.34
select round(2.35,2)
输出2.35

```



##### 6.具体案例：

通过数据库的函数，生成一个六位数的随机验证码。

少用，一般是开发语言搞得

```sql
select lpad(round(rand()*1000000,0),6,"0");

lpad补0，因为0.012345会变成5位数12345，需要补0：123450
```



### 3.日期函数

#### 常见日期函数

| curdate()                         | 返回当前日期                                      |
| --------------------------------- | ------------------------------------------------- |
| curtime()                         | 返回当前时间                                      |
| now()                             | 返回当前的日期和时间                              |
| year(date)                        | 获取指定date的年份                                |
| month(date)                       | 获取指定date的月份                                |
| day(date)                         | 获取指定date的日期                                |
| date_add(date,interval expr type) | 返回一个日期/时间值加上一个时间间隔expr后的时间值 |
| datediff                          | 返回起始时间date1和结束时间date2之间的天数        |

##### 案例演示：

```sql
select curdate();

select curtime();

select now();

year(date) month(date) day(date)
select year(now());
2025
select month(now());
8
select day(now());
3

求当前时间往后70天
select date_add(now(),interval 70 day);
求当前时间往后70月
select date_add(now(),interval 70 month);
求当前时间往后70年
select date_add(now(),interval 70 year);


select datediff('2021-12-01','2021-11-01')
输出：30
select datediff('2021-12-01','2021-10-01')
输出：61
select datediff('2021-10-01','2021-12-01')
输出：-61
```



查询所有员工的入职天数，并根据入职天数倒序排序。

entrydate 入职时间

```sql
select
	datediff(curdate(),entrydate) as "入职天数"
form emp
	order by 入职天数 desc;
```





### 4.流程函数

流程函数也是很常用的一类函数，可以在SQL语句中实现条件筛选，从而提高语句的效率。

| if(value,true,false)                                  | 如果value为true，则返回t，否则返回f               |
| ----------------------------------------------------- | ------------------------------------------------- |
| ifnull(value1,value2)                                 | 如果value1不为空，返回value1，否则返回value2      |
| case when [value1] then [res1].....else [default] end | 如果val1为true，返回resl，..否则返回default默认值 |
|                                                       |                                                   |

```sql
select if（true，'ok'，'Error'）;
输出：ok
select if（false，'ok'，'Error'）;
输出：error

-- ifnull
select ifnull('ok','Default');
返回ok
select ifnull（'','Default'）;
返回''
select ifnull(null,'Default');
返回Default



case when then else end使用案例：
B域4A账号分布:
 when c.user_type = '00' then   '未知帐号'  
 when c.user_type = '01' then   '普通帐号'
 when c.user_type = '02' then   '程序帐号'   
 when c.user_type = '03' then   '系统帐号'
 when c.user_type = '04' then   '管理帐号'  
 when c.user_type = '05' then  '资源管理帐号'     
 when c.user_type = '06' then   '超级帐号' 
 when c.user_type = '07' then   '运维账号' 
 else c.user_type
 end 从帐号类型

```

![image-20250803162812390](https://raw.githubusercontent.com/Romantic-1/ImgBed/main/20250803162812650.png)



##### 案例：

```sql
案例：统计班级各个学员的成绩，展示的规则如下：
>=85，展示优秀
>=60，展示及格
否则，展示不及格

建表sql语句：
create table score(
	id int comment 'ID'，
	name varchar(20)  comment‘姓名'，
	math int comment ‘数学',
	english int comment ‘英语',
	chinese int comment '语文'
)comment 学员成绩表；
```

![image-20250803163152823](https://raw.githubusercontent.com/Romantic-1/ImgBed/main/20250803163153080.png)





## 3.8 约束

### 1.概述

概念：约束是作用于表中字段上的规则，用于限制存储在表中的数据。

目的：保证表中数据的正确性，有效性和完整性

#### 常见的约束

| 非空                       | 限制该字段的数据不能为null                     | NOT NULL    |
| -------------------------- | ---------------------------------------------- | ----------- |
| 唯一                       | 保证该字段的所有数据都是唯一、不重复的         | unique      |
| 主键                       | 主键是一行数据的唯一                           | primary key |
| 默认约束                   | 保存数据时，如果未指定该字段的值，则采用默认值 | default     |
| 检查约束（8.0.16版本之后） | 保证字段值满足某一个条件                       | check       |
| 外键约束                   | 用来让两张表的数据之间建立连接，保证数据的     | foreign KEY |

注意：约束是作用于表中字段上的，可以在创建表/修改表的时候添加约束。



### 2.约束演示

#### 案例：

根据需求完成表结构的创建

![image-20250803213535266](https://raw.githubusercontent.com/Romantic-1/ImgBed/main/20250803213535521.png)

id------->primary key  和auto_increment

name--------> not null 和unique

age----------->check

status--------> default

gender-------->无约束

```sql
create table user(
   id int primary key auto_increment comment "id主键",
   name varchar(10) not null unique comment "姓名",
   age int check( age>0 && age <= 120) comment "年龄",
   status char(1) default "1" comment "状态",
   gender char(1) comment "性别"
)comment "用户表";
```

插入数据验证：

```sql
insert into user(name,age,status,gender)
				values('tom1',19,'1','男')

insert into user(name,age,status,gender)
				values('tom2',25,'0','男')
				
insert into user(name,age,status,gender)
				values(null,25,'0','男')	
     
insert into user(name,age,status,gender)
				values("tom2",25,'0','男')		
				

```

![image-20250803214148205](https://raw.githubusercontent.com/Romantic-1/ImgBed/main/20250803214148462.png)

![image-20250803214237260](https://raw.githubusercontent.com/Romantic-1/ImgBed/main/20250803214237517.png)

验证age和status字段

![image-20250803214449805](https://raw.githubusercontent.com/Romantic-1/ImgBed/main/20250803214450056.png)





### 3.外键约束

#### 1.概念

外键用来让两张表的数据之间建立连接，从而保证数据的一致性和完整性。

注意：目前上述的两张表，在数据库层面，并未建立外键关联（物理外键），所以是无法保证数据的一致性和完整性的。

![image-20250803214749150](https://raw.githubusercontent.com/Romantic-1/ImgBed/main/20250803214749431.png)

假如，我们删除了部门表的id为1的研发部，但是在数据库层面，并未建立外键关联。所以员工表不会有任何变化

但是如果建立了外键关联，删除了部门表的id为1的研发部,会出现报错，不能删除数据，因为存在外键关联





![image-20250803215001648](https://raw.githubusercontent.com/Romantic-1/ImgBed/main/20250803215001914.png)







#### 2.建立外键关联语法

##### 建表的时候建立

```sql
create table user(
   .....
   [constraint] [外键名称] foreign key (外键字段名) references 主表 (主表列名)
);
```



##### 修改表结构的时候建立

```sql
alert table 表名 add constraint 外键名称 foreign key (外键字段名) references 主表 (主表列名)

alert table emp add constraint fk_emp_dept_id foreign key (dept_id) references dept(id);
```

![image-20250803215932105](https://raw.githubusercontent.com/Romantic-1/ImgBed/main/20250803215932369.png)

![image-20250803214749150](https://raw.githubusercontent.com/Romantic-1/ImgBed/main/20250803214749431.png)

#### 3.删除外键

```sql
alert table 表名 drop foreign key 外键名称;
alert table 表名 drop foreign key fk_emp_dept_id;
```

![image-20250803220230419](https://raw.githubusercontent.com/Romantic-1/ImgBed/main/20250803220230685.png)



#### 4.外键的           删除和更新行为

![image-20250803220358771](https://raw.githubusercontent.com/Romantic-1/ImgBed/main/20250803220359051.png)

restrict限制 cascade级联

在数据库中删除一个记录可能会自动删除所有依赖于它的记录，这被称为级联删除。



no action = restrict 首先检查该记录是否有对应外键，如果有则不允许删除/更新。

cascade 首先检查该记录是否有对应外键，如果有，则也删除/更新外键在子表中的记录。

set null 当在父表中删除对应记录时，首先检查该记录是否有对应外键，如果有则设置子表中该外键值为null（这就要求该外键允许取null）

ser default 父表有变更时，子表将外键列设置成一个默认的值（lnnodb不支持）



##### 如何约束外键删除更新的行为

```sql
alter table 表名 add constraint 外键名称 foreign key （外键字段）preferences 主表名（主表字段名）on update cascade  on delete cascade ;
```

![image-20250803221205126](https://raw.githubusercontent.com/Romantic-1/ImgBed/main/20250803221205438.png)

```sql
alter table 表名 add constraint 外键名称 foreign key （外键字段）preferences 主表名（主表字段名）on update cascade  on delete cascade ;
```

![image-20250803221409636](https://raw.githubusercontent.com/Romantic-1/ImgBed/main/20250803221409930.png)



set null:

![image-20250803221636952](https://raw.githubusercontent.com/Romantic-1/ImgBed/main/20250803221637256.png)

