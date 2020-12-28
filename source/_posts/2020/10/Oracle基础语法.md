---
title: Oracle基础语法
date: 2020-10-13 19:08:41
tags: SQL
categories: "SQL"
top_img:
cover: https://gitee.com/wang_hong_bin/pic-go-photos/raw/master/oracle.jpg
---

#### Oracle 11g :
<font color='red'>注：此笔记为个人在学习Oracle时从教学视频、练习整理</font>
>  <font color='red'>安装问题: </font>
>  + 在安装完成后如果遇到口令管理无法出现那么就需要手动配置数据库
>  1.  <font color='green'>找到Oracle 安装中出现的 Database Configuration Assistant</font> 
>  2. 进行手动配置数据库(默认操作) -- 完成<font color='red'>口令管理</font>

>  <font color='red'>图形化界面助手(SQLDEVELOPER)安装问题: </font>
>
>  + TNS 加载出错，找到安装路径进行对后缀名为点 <font color='red'>ora</font>文件进行查看。(主要是对端口看，全局数据库名查看)

#### 目录:
+  用户创建并赋予基础权限
 ```sql
 	--  显示当前连接用户
 	show user;
	-- 创建用户 student
	create user student identified by student;
	-- 对用户 student 赋予权限
	grant create session to student;
	grant connect,resource to student;
 ```
```sql
-- 解锁用户
alter user 解锁用户名 account unlock;
```

#### 表的增删改查练习:
+ <font color='red'>注： ROWID Oracle特有可自行查阅理解</font>
```sql 
-- 查询 emp 表的最小 ROWID 
select min(rowid) from emp;
```
+ Oracle 常用的几个函数：
```sql
desc 表名;
-- 作用介绍：
在已创建表的基础上插入值的时候会出现数据类型不匹配，可以通过 desc 表名 显示字段的数据类型，快速插入匹配的数据记录
```
#### 表空间：
```sql
   select file_name,tablespace_name
2  from dba_data_files
3  order by tablespace_name;
```


#### 修改表空间(新增数据文件):
```sql
alter TableSpace 文件名 add  DataFile  'd；/文件名02.dbf' size 10m Autoexitend
on next 10m maxSize z;  
```

#### 增加表空间N的大小: 调整数据文件
```sql
alter database datafile '文件名01.dbf'
autoextend on next Y maxsize Z;
```
### 创建数据表:
+ 关系模式到关系表的映射:

|  概念模型  |     关系表     |
| :--------: | :------------: |
|    元组    |      记录      |
|    属性    |     字段名     |
|   属性值   |     字段值     |
|     域     | 数据类型及长度 |
| 码、候选码 |  主键、关键字  |

+ Oracle数据类型；

|      类型       |   说明   |
| :-------------: | :------: |
|     CHAR(n)     | 定长字符 |
|   VARCHAR2(n)   | 变长字符 |
| NUMBER([n],[m]) |   数值   |
|      DATE       |   日期   |

#### Oracle日期型:
```sql
-- 获取当前系统的时间
SELECT TO_CHAR(SYSDATE,'yyyy-mm-dd hh24:mi:ss') FROM dual;

 --日期转化为字符串  
SELECT TO_CHAR(SYSDATE,'yyyy-mm-dd hh24:mi:ss') AS NOWTIME FROM DUAL;  
 	-- 获取时间的年
SELECT TO_CHAR(SYSDATE,'yyyy') AS NOWYEAR   FROM DUAL;      
   -- 获取时间的月   
SELECT TO_CHAR(SYSDATE,'mm')    AS NOWMONTH FROM DUAL;   
 -- 获取时间的日  
SELECT TO_CHAR(SYSDATE,'dd')    AS NOWDAY    FROM DUAL;    
    -- 获取时间的时 
SELECT TO_CHAR(SYSDATE,'hh24') AS NOWHOUR   FROM DUAL;     
    -- 获取时间的分  
SELECT TO_CHAR(SYSDATE,'mi')    AS NOWMINUTE FROM DUAL;  
   --获取时间的秒
SELECT TO_CHAR(SYSDATE,'ss')    AS NOWSECOND FROM DUAL;  

-- 插入特定格式日期
to_date('2020-02-20','yyyy-mm-dd');
```

#### 创建表:
```sql
create table tableName(
	-- 用户id
	id number nut null primary key,
	-- 用户名
	userName char(6) not null,
	-- 用户性别
	sex varchar2(3),
	-- 用户生日
	birthday date
);
-- 对表 tableName 插入对应的值
insert into tableNmae values(1,'aidou','男',to_date('2020-02-20','yyyy-mm-dd'));
```
#### 表名更新:
```sql
alter table oldTableName rename to newTableName;
```
#### 字段名添加：
```sql
 alter table tableNmae add(字段名 数据类型);
```
#### 连接 ( || )：
```sql
案例: 编号是: 7369 的雇员，姓名是: Tom, 工作是: Clean;
    select '编号是: ' || empno || '的雇员,姓名是: ' || ename ||', 工作是: ' || job from emp;
    编号是: 7369 的雇员，姓名是: , 工作是: ;
```

 > 数据库不仅仅是存储数据，他还必须保证所有的数据的正确性，为了维护数据库中数据的完整性，在创建表的时候常常需要定义一些约束。

 ```sql
 Oracle 11g 的六大约束:
        + 非空约束 not null 
        + 主键约束 primary key
        + 唯一约束 unique
        + 外键约束 foreign key
        + 检查约束 check
        + 默认约束 default 
 ```

#### 非空约束:
```sql
    -- 非空约束
    -- 添加非空约束：
       alter table 表名 modify 字段名 not null
   -- 删除某字段的非空约束，其实就是允许字段为空
       alter table modify 字段名 null
```

#### 主键约束:
```sql
    -- 主键约束
    -- 添加主键约束：
        alter table 表名 add constraint PK_主键名 primary key(字段名);
    -- 删除主键约束:
        alter table 表名 drop constraint 主键名;
```

#### 唯一性约束:
```sql
    -- 添加唯一性约束:
        alter table 表名 add constraint 名_UK unique(字段名);
    -- 删除唯一性约束:
        alter table 表名 drop constraint 名_UK; 
```

#### 外键约束:
```sql
    -- 外键约束会使用两个表进行关联，外键是指 "当前表" 引用 "另外一个表"(即被引用表)的某个列，
    -- 而被引用的列必须具有主键约束或唯一性约束 
        alter table 当前表 add constraint FK_名 foreign key(引用字段名) references 被引用表表名(被引用字段名);
    
    -- 创建表的时候创建约束:
    create table xx表(
        no number not null,
        QQ varChar2(20),
        -- 外键约束的添加
        constraint FK_名 foreign key(引用字段名) references 被引用表表名(引用的字段名) 
    );
        alter table 表名 drop foreign key 外建名；
```

#### 检查约束:
```sql
 -- 创建一个书本信息表,给价格添加 check 约束
 create table bookInfo(
     bookId number,
     nookName char,
     price number,
     author char,
     -- 添加检查约束:
     constraint ck_名 check([检查约束表达式表达式] price>=10 and price <=100>)
 );

-- 对表的某字段进行添加 check 约束
    alter table 表名 add constraint ck_名 check( [检查约束表达式表达式] );
-- 删除 check 约束
    alter table 表名 drop constraint  ck_age;
```

#### 默认约束
```sql
    create table 表名(
        name varchar2(10) not null,
        id number(10),
        sex varchar2(10),
        age number(5) default 18
    );
-- 对 xx表 的字段添加默认约束
    alter table 表名 modify 字段 default '默认条件'
```

#### 查询表中的约束:
```sql
-- 查询整张表的约束:
    select * from user_constraints where table_name = '要查询表的表名'
-- 单一字段的约束查询:
    select constraint_name from user_cons_columns where table_name = '要查询表表名' and column_name = '要查询列的字段名';
```
#### 模糊查询:
```sql
like 
between and 
in 
is null | is not null
```

+ like 一般与通配符连用(%查询内容%) 任意多个字符，包含 0 个字符.
```sql
-- scott表中查询
-- 案例一:
查询员工名中包含字符A的员工信息
SELECT * FROM EMP WHERE ENAME LIKE '%A%';
```

+ 通配符 _ 的使用:(下划线占位，位置后放要查询包含的字符)
```sql
-- 查询 emp 表中ename 中第一个字符包含A,第三个字符包含 L的人员和工资
SELECT ENAME,SAL FROM EMP WHERE ENAME LIKE 'A_L%' AND SAL>200;
```

+ 查询员工命中第二个字符为 _ 的员工名(转义字符的使用)
```sql
 SELECT ENAME FROM EMP WHERE ENAME LIKE '_\_%'

-- ESCAPE 的用法
 SELECT ENAME FROM EMP WHERE ENAME LIKE '_$_%' ESCAPE '$';
```

+ between and 优点:
  + 提高语句可读性
  + 临界值包含且不能颠倒 
  
```sql
  -- 查询员工姓名,员工工资在 1500 ~ 5000的人员信息
  SELECT ENAME,SAL FROM EMP WHERE SAL>=1500 AND SAL <=5000;
  -- between and 简介优化语句
  SELECT ENAME,SAL FROM EMP WHERE SAL BETWEEN 1500 AND 5000;
```

+ 关键字 in
+ 含义: 判断某字段的值是否属于 in 列表中的某一项
+ 特点:  使用 in 提高语句简洁度
+ in 列表的值类型必须一致(不支持通配符使用)

```sql
  --查询员工姓名，以及员工工资在 1600 2450 3000 的人员信息
  SELECT ENAME,SAL FROM EMP WHERE SAL = 1600 OR SAL = 2450 OR SAL = 3000;
  -- in  语句优化
  SELECT ENAME,SAL FROM EMP WHERE SAL IN('1600','2450','3000');
```

+ IS NULL 的使用:
  
```sql
 -- 查询 emp 表中comm 为 null 的人员信息
 SELECT ENAME,COMM FROM EMP WHERE COMM IS NULL;  
```

+ IS NOT NULL 的使用:
+ = 或 <> 不能判断 NULL
#### 初见case：
```sql
 -- 类似于 SWITCH CASE 
 -- ORACLE : 
 -- CASE 要判断的字段或表达式
 -- WHEN 常量1 THEN 要显示的值 1或语句1；
 -- WHEN 常量2 THEN 要显示的值 2或语句2
 -- ELSE 要显示的值 N 或语句 N;
 -- END
 
 --  查询 员工的工资，要求:
 /*
 部门号 = ，显示的工资为1.1 倍
 部门号 = ，显示的工资为1.2 倍
 部门号 = ，显示的工资为1.3 倍
 其他部门，显示的工资为原工资
 */
 SELECT * FROM EMP;
 SELECT SAL 原始工资,EMPNO,CASE EMPNO  
 WHEN 7369 THEN SAL*1.1
 WHEN 7521 THEN SAL*1.2
 WHEN 7654 THEN SAL*1.3
 ELSE SAL
 END AS
 FROM EMP;
 
 --case 函数的使用二: 类似于 多重 if
 /*
 case 
     when 条件1 then 要显示的值 1 或语句 1 
     when 条件2 then 要显示的值 1 或语句 2
  	  else  要显示的值 n 或 语句 m
 end
 
 */
````
```sql
 --   案例
 
 /*
  如果工资 > 1300,显示 A 级别
  如果工资 > 1500,显示 B 级别
  如果工资 > 1900,显示 C 级别
  否则 ，显示 D 级别
 */

 SELECT ENAME,SAL,CASE 
 WHEN SAL > 1300 THEN 'A'
 WHEN SAL > 1600 THEN 'B'
 WHEN SAL > 3000 THEN 'C'
 ELSE 'D'
 END AS 工资级别
 FROM EMP;

 -- 查询员工工号，姓名，工资，以及工资提高20%后的结果(NEW SALARY)
 SELECT ENAME,EMPNO,SAL *1.2 "NEW SALARY" FROM EMP;

 -- 将员工的姓名按首字母排序，并写出姓名的长度(length)
 SELECT LENGTH(ENAME) 姓名长度,SUBSTR(ENAME,1,1) 姓名首字符,ENAME FROM EMP ORDER BY SUBSTR(ENAME,1,1) ASC;

-- 字符串拼接 做一个查询，产生下面的结果
SELECT CONCAT(ENAME,' earns  ',SAL,'  monthly but wants ',SAL*3) AS "Dream Sal" FROM EMP WHERE SAL=3000;

-- 使用case -- when 按照下面的条件
SELECT EMPNO AS JOB ,
CASE EMPNO
WHEN 7369 THEN  'A'
WHEN 7499 THEN  'B'
WHEN 7566 THEN  'C'
END AS GRADE
FROM EMP
WHERE EMPNO='7369';
```

```sql
  -- 检查表结构
  
    DESC SCORE;
  
  ---- 创建Score 表
    
    CREATE TABLE SCORE(
    NAME VARCHAR(50)  PRIMARY KEY DISABLE,
    DEGREE  INT ,
    SEX  VARCHAR(10)
    );
  
  --查询表 score 
   SELECT * FROM SCORE;
  -- 添加信息 insert into 表名 values()
   INSERT INTO SCORE VALUES('aidou',78,'男');
  -- 查询 Score 表
    SELECT * FROM SCORE;
  
  -- 在表Score 中插入 85 86 88 的成绩；
    INSERT INTO SCORE VALUES('菠萝',85,'男');
    INSERT INTO SCORE VALUES('水蜜桃',88,'女');
    INSERT INTO SCORE VALUES('苹果',86,'男');
  
  -- 查询表Score 再次添加的结果;
   SELECT * FROM SCORE;
  
  -- 由于误操作，多插入一条记录，删除记录；
   DELETE FROM SCORE WHERE NAME='苹果' AND SEX='男';
  
  --再次查看 Score 结构;
   SELECT  *  FROM SCORE;
  
  -- 再次插入 86分的记录
   INSERT INTO SCORE VALUES('苹果',86,'女');
  
  --  查看
   SELECT * FROM SCORE;
  
  -- 查询指定记录
   SELECT * FROM SCORE WHERE DEGREE IN( '85','86','88');
  
   Desc Help;
```




```sql
-- 创建 STDUENT 表

  CREATE TABLE STUDENT
  (
    SNO CHAR(6) PRIMARY KEY,
    SNAME VARCHAR2(12),
    DEPT VARCHAR2(20),
    SEX VARCHAR2(3)
  );

-- 查询 STDUENT 表
  SELECT * FROM STDUENT;
  
-- 向 STDUENT 表中插入记录
 INSERT INTO STDUENT(SNO,SNAME,DEPT,SEX)  VALUES('293261','aidou','计算机信息管理','男')
   
-- 插入记录成功后再次查询表结构
  SELECT * FROM STDUENT;

-- 删除记录
DELETE FROM STUDENT WHERE SNO='193161' AND SNAME='王宏斌';

-- 查询已经删除后表的结构
SELECT SNO,SNAME,SEX FROM STDUENT WHERE SNO='193161' AND SEX='男' AND SNAME='王宏斌'
  
SELECT * FROM STUDENT;
```
#### 常见函数:
```sql

-- 查询 EMP 表 所有人的工资总和以及最高和最低以及平均工资
SELECT SUM(SAL) 求和,ROUND(AVG(SAL),2) 平均工资,MAX(SAL) 最大工资,MIN(SAL) 最低工资,COUNT(SAL)  领取工资人数 FROM EMP;

-- 参数支持那些类型


-- 是否忽略 NULL
SELECT SUM(COMM) 求和,ROUND(AVG(COMM),2) 平均工资,MAX(COMM) 最大工资,MIN(COMM) 最低工资,COUNT(COMM)  领取工资人数 FROM EMP;

-- 和 DISTINCT 搭配
SELECT SUM(DISTINCT SAL),SUM(SAL) FROM EMP;

SELECT COUNT(DISTINCT SAL),COUNT(SAL) FROM EMP;

-- COUNT 函数的详细介绍
SELECT COUNT(SAL) FROM EMP;
-- 统计个数 COUNT(*)
SELECT COUNT(*) FROM EMP;
SELECT COUNT(1) FROM EMP;

-- 和分组函数一同查询的字段有限制


-- 查询员工工资的最大值，最小值，平均值，总和
SELECT MAX(SAL) 最大工资,MIN(SAL) 最小工资,ROUND(AVG(SAL),2) 平均工资,SUM(SAL) 总工资 FROM EMP;


-- 查询部门编号为 7369 的员工个数
SELECT COUNT(*) FROM EMP WHERE EMPNO='7369';

SELECT * FROM EMP;

```

#### <font color='red'>限制行数查看:</font>
```sql
-- Eg. 显示 Oracle 数据库 EMP表的前三行数据
select * from EMP  where rownum<4;
```