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
 + 怎么创建(使用DDL):   
 ```
 
 ```

# NESTJS基础