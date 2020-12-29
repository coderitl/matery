---
title: Oracle-日常积累
tags: SQL
categories: SQL
password: ''
abstract: 'Something is encrypted, please enter the password to view.'
message: 'Hello, password is required here'
wrong_pass_message: 'Sorry, this password doesn''t look right, please try again.'
wrong_hash_message: >-
  Sorry, this article cannot be verified, but you can still see the decrypted
  content
abbrlink: 34230
date: 2020-12-16 16:18:18
top_img:
cover:
---

###  Oracle-日常积累

+ 日期格式应用

  ```sql
  -- 删除表 testTable
      drop table testTable;
  -- 创建表
      create table testTable(str_time DATE);
      desc testTable;
         -- 插入数据
          insert into testTable values(to_date(to_char(sysdate,'yyyy-mm-dd hh24:mi:ss'),'yyyy-mm-dd hh24:mi:ss'));
          -- 查询数据
          select to_char(str_time,'yyyy-mm-dd hh24:mi:ss') from testTable; 
          commit;
  ```

+ 数据分页

  ```mysql
  
  ```

+ 学员信息查询

  ```sql
  -- 删除表
  drop table student;
  -- 创建学生表
      create table student(
          -- 编号
          id int,
          -- 姓名
          name varchar2(10),
          -- 课程
          cource varchar2(10),
          -- 成绩
          score int
      );
  -- 数据插入
      insert into student values(1,'张三','语文',81);
      insert into student values(2,'张三','数学',75);
      insert into student values(3,'李四','语文',81);
      insert into student values(4,'李四','数学',90);
      insert into student values(5,'王五','语文',81);
      insert into student values(6,'王五','语文',100);
      insert into student values(7,'王五','英语',90);
  -- 查询数据
      select * from student;
  -- 查询每门课程都考了并且成绩大于 80 分的学生信息
      -- 统计课程数
          select count( distinct cource) from student;
      -- 修改数据
          update student  set cource = '数学' where id = 6;
      -- 查询课程都考了并且成绩大于 80 的人员信息
      select name from student
          group by name 
          having min(score)>80 and count(distinct cource) = ( select count( distinct cource) from student);
  
  ```

  