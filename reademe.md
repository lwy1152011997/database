# 数据库(Database)基础  
1. 是什么?  
    是按照数据结构来组织，存储和管理数据的仓库  
    专业的数据库是专门对数据进行创建，访问，管理，搜索等操作的软件

2. 有什么用?  
    + 对数据进行持久化的保存  
    + 方便数据的存储和查询，速度快，安全，方便  
    + 可以处理并发访问  
    + 更加安全的权限管理访问机制  

3. 有哪些类型?  
    关系型数据库:  
        + MySQL（被Oracle收购），Oracle，SQLserver...  
    非关系型数据库:  
        + Redis内存数据库，MongoDB文档数据库  

4. 长什么样的?  

5. 主要介绍MySQL和MongoDB  
```
MySQL:  
本地安装包安装: https://blog.csdn.net/qq_59636442/article/details/123058454

MongoDB: https://blog.csdn.net/crsitin_spade/article/details/121383699
本地安装包安装:
```

6. 几个术语:  
    + DB(数据库)  
    + DMBS(数据库软件管理系统: 比如MySQL和MongoDB的可视化软件)  
    + SQL(数据库的专用语言)  
    
## MySQL  
+ 优点:  
    1. 免费  
    2. 快速  
    3. 容易安装和使用  

+ 基本结构:  
![](./%E6%95%B0%E6%8D%AE%E5%BA%931.awebp)
![](./%E6%95%B0%E6%8D%AE%E5%BA%932.awebp)

+ 登录  
使用命令(首次): `mysql -u root`  
退出命令: `exit`  
登陆成功后有提示:  
![](./%E7%99%BB%E5%BD%95%E6%8F%90%E7%A4%BA.png)  
![](./%E7%99%BB%E5%BD%952.png)  

使用命令: `show databases;` (注意后面有一个分号和npm不同)查看基本结构  
![](./%E5%9F%BA%E7%A1%80%E6%95%B0%E6%8D%AE%E5%BA%93.png)

+ 图形化界面: Navicat(http://www.navicat.com.cn/download/direct-download?product=navicat_premium_cs_x64.exe&location=1)  
![](./navicat%E7%95%8C%E9%9D%A2.png)

## SQL语言:
1. 是什么?  
    全称: Structured Query Language 结构化查询语言 的缩写  
    是和数据库进行交互的语言, 操作关系型数据库, 也是数据库的规范  

2. 分类:  
    + 数据定义 DDL  Data Definition Langue 用在: 定义数据库,表, 视图, 索引  
    + 数据操纵 DML       Manipulation      用在: 数据库的表中进行 增加/删除/修改 操作  
    + 事务控制 TCL  Transaction Control    用在: 数据库中的事务管理(?? 事务管理还没有太理解)  
    + 数据查询 DQL       Query             用在: 查询数据库中的数据  
    + 数据控制 DCL       Control           用在: 控制数据库用户权限

3. 语法书写:  
    + 不区分大小写  
    + 关键字使用大写  
    + 数据库名, 表名, 列名 建议使用小写  
    + 可写多行或者一行, 使用空格和缩进可以增强语句的可读性, 结束用;分号  
    + 注释: # 单行  /* xxx */ 多行  

 4. 关键字: `https://blog.csdn.net/yinni11/article/details/79859659`  

*****************对数据库的操作********************

 ## 创建数据库:
 + 怎么创建(使用DDL):  
 ```
 直接创建数据库:
 CREATE DATABASE mydatabase  
 CREATE DATABASE IF NOT EXISTS mydatabase  
 ```
![](./%E7%9B%B4%E6%8E%A5%E5%88%9B%E5%BB%BA%E6%95%B0%E6%8D%AE%E5%BA%931.png)  
![](./%E7%9B%B4%E6%8E%A5%E5%88%9B%E5%BB%BA%E6%95%B0%E6%8D%AE%E5%BA%932.png)  

```
指定字符集的方式创建:  
CREATE DATABASE [IF NOT EXISTS] mydatabase CHARACTER SET 字符集(UTF8万国码, GBK, GB2312, ...https://zhuanlan.zhihu.com/p/401819870)
 创建的数据库指定内存放的限制字符集
```

```
指定字符集和排序规则的方式创建:  
CREATE DATABASE [IF NOT EXISTS] mydatabase CHARACTER SET 字符集 COLLATE 排序规则(规则: https://blog.csdn.net/fengye_csdn/article/details/109523317)
```

## 查看数据库:
```
查看全部数据库名:
SHOW databases;

查看指定的数据库名:
SHOW CREATE DATABASE mydatabase;
```

## 修改和删除数据库:
注意点: 只能修改数据库的字符集和排序规则, 不能修改数据库名  
```
ALTER DATABASE mydatabase CHARACTER SET[COLLATE 排序规则]
```

## 使用数据库:
```
步骤:
1.先切换: USE mydatabase;
2.在查看: SELECT DATABASE();
```

*****************对表的操作**************************
 ## 创建表:
 + 表是一种数据库的对象, 由若干个字段(列)组成

 + 怎么创建(使用DDL, 在创建表之前, 我们需要先使用数据库):   
 ```
 CREATE TABLE 表名 (字段1 数据类型, 字段2 数据类型, 字段3 数据类型, 字段4 数据类型, ... 数据类型, 字段n 数据类型) 
 或者写成:
 CREATE TABLE 表名 (
     字段1 数据类型,
     字段2 数据类型,
     字段3 数据类型,
     字段4 数据类型,
     ... 数据类型,
     字段 数据类型n
 )

 创建一个人的表:
 CREATE TABLE maiGuaRen (
     id INT,
     name VARCHAR(20),
     age INT
 )
 ```  

 ## 表中的数据类型:
 1. 常见的数据类型:
    + 数值型  
    + 字符型  
    + 日期型  
 `参考链接: https://blog.csdn.net/Txixi/article/details/115207570`

 ```
 创建表:  
 1. 先创建数据 CREATE DATABASE demodb1
 2. 使用数据库 USE demodb1
 3. 选择数据库 SELECT DATABASE()
 4. 创建表 
 CREATE TABLE people (
     id INT,
     name VARCHAR(20),
     age date
 )
 5. 查看表
 ```

 ## 查看表:
+ 查看表: `show tables`  
+ 查看表结构: `DESC 表名`  
+ 查看创建表的SQL语句(也就是这个表是执行什么样的SQL语句创建出来的): `SHOW CREATE TABLE 表名;`  
+ 复制表结构: `CREATE TABLE 新表名 LIKE 旧表名`

## 修改表(主要是修改字段(列)的数据):  
+ 添加新的一列(字段): `ALTER TABLE 表名 ADD 字段 类型`  
+ 修改列(字段)的名: `ALTER TABLE 表名 CHANGE 旧字段 新字段 类型`  
+ 修改列(字段)的类型: `ALTER TABLE 表名 MODIFY 字段 新类型`  
+ 删除指定列(字段): `ALTER TABLE 表名 DROP 列名`  

+ 修改表名: `RENAME TABLE 表名 TO 新表名`  
+ 删除表: `DROP TABLE 表名`  

## DML语句对表的操作: 
`解释: DML语句 是对 表中的数据进行 增 删 改 的操作`
1. 增:  
    + 将指定字段插入表中(key-value 需要一一对应): INSERT INTO 表名 (字段1, 字段2, 字段3...) VALUES (1值, 2值, 3值...)  
    + 不指定字段插入表中(顺序和创建的表的字段顺序一一对应): INSERT INTO 表名 VALUES (1值, 2值, 3值...)  

2. 复制数据:  
    + INSERT INTO 表名a SELECT * FROM 表名b

3. 改(更新):  
    + 不带更新条件(整个列的值都会变): `UPDATE 表名 SET 字段1=值1,字段2=值2,字段3=值3...`  
    + 带条件的: `UPDATE 表名 SET 字段1=值1 WHERE 条件`

4. 删:  
    + 带条件的: `DELETE FROM 表名 WHERE 条件`  
    + 不带条件的: `DELETE FROM 表名`  

## DQL语句对表的查询: 
1. 是干嘛的?  
用来查询数据库中的数据, 不会对数据库的内容进行修改, 可理解为仅是一个get操作  

2. 简单查询:  
     + 查询表中的全部数据(查询表中的所有列): `SELECT * from 表名`  
     + 查询指定字段(有限使用这种): `SELECT 字段1, 字段2,字段3,... FROM 表名`  
     + 别名查询(给列或者表取个名, 好处是方便查看和处理查到的数据):  
     `SELECT 字段名1 AS 别名1, 字段名2 AS 别名2,... FROM 表名`  
     `SELECT 字段名1 AS 别名1, 字段名2 AS 别名2,... FROM 表名 AS 别名`  
     ```
     AS 可以省略
     SELECT name AS myname FROM people
     省略: SELECT name 'myname' FROM people
     // 表取别名一般是在多表进行联查的时候用到, 现在我暂时还不会, 后续再补充
     ```  

3. 去除重复数据:  
    ```
    再查询某个指定的字段时,它的值可能会有多个相同的, 默认查询的时候都会全部显示出来
    确认数据是否重复,需要指定列的维度来进行确认

    语法:
        SELECT DISTINCT 字段1,字段2,... FROM 表名
    ```  

 4. 将查询结果参与运算:  
    ```
    就是将查询结果的列中的可进行计算的值进行 加减乘除数学操作, 这个操作不会影响数据库中的存储数据, 只会影响展示结果

    语法:  
        SELECT 列名1 +固定值 FROM 表名  单列计算
        SELECT 列名1 + 列名2 FROM 表名 多列计算
    
    exp:  
         SELECT age-10 FROM people;
         SELECT moeny + nomoeny FROM people;
    ```

 ## 条件查询(WHERE):  
1. 比较运算符:  
    + 等于 =  
    + 大于 >  
    + 小于 <  
    + 大于等于 >=  
    + 小于等于 <=  
    + <> 和 != 表示不等于  
    + `语法: SELECT * FROM 表名 WHERE 查询条件`
    查询全部身上的钱多余10块的: `SELECT * FROM people WHERE money > 10`  

2. 逻辑运算:  
    + AND(&&) 多个条件同时满足  
    + OR(||) 满足其中一个  
    + NOT(!) 不满足  
    + `语法: SELECT * FROM people WHERE money>10 AND age>20`  

3. 指定查询范围:  
    `关键字: IN BETWEEN`
    `语法: SELECT 字段名 FROM 表名 WHERE 字段 IN (数据1, 数据2, ...)`  
    ```
    解释: IN的使用类似于查询的条件使用了多个 OR 进行连接
    例:
    查询 身上有10 20 30 块钱的人:
    SELECT * FROM people WHERE money IN (10, 20 ,30);

    查询 身上没有10 20 30 块钱的人:
    SELECT * FROM people WHERE money NOT IN (10, 20 ,30);

    查询岁数20~30岁的人:
    SELECT * FROM people WHERE age>=20 AND age<= 30;
    SELECT * FROM people WHERE age BETWEEN 20 AND 30;
    ```  

4. 模糊查询:  
    `语法: SELECT * FROM 表名 WHERE 字段 LIKE '通配符字符串'`  
    通配符:  
    + % 表示任意个字符匹配
    ```
    %号的解释:  
    比如要匹配 NBA CBA CUBA WNBA WCBA NCAA 这几项
    %A 此时的%匹配了A的左边的0~N个字符 就能找到6个结果
    AA% 此时以AA开始为基础匹配进行匹配, 以上没有以AA开始的所以为0个结果
    %N% 当中只要包含N都能就行匹配 3个结果;
    ```
    + _ 标识语个字符匹配  
    ```
    _号的解释:
    比如要匹配 NBA CBA CUBA WNBA WCBA NCAA 这几项
    我要匹配 NBA
    SELECT * FROM people WHERE name LIKE '_BA' 只能匹配到 NBA CBA 一个_就是一个字符
    ```
    
    ```
    示例:  
    查询姓刘的人:  
    SELECT * FROM people WHERE name LIKE '刘%'

    查询名字中包含文的人:  
    SELECT * FROM people WHERE name LIKE '%文%'
    ```

# NESTJS基础