---
title: Mybatis CURD
date: 2020-10-13 19:12:33
tags: SQL
categories: "SQL" #分类
top_img:
cover: https://gitee.com/wang_hong_bin/pic-go-photos/raw/master/mybatis.jpg
---

### User类(只需要写数据库中对应的字段名，通过IDEA 快捷键 `Alt + ins`) 快速实现 `setxxx`方法 和 `toString()`:
```java
package com.ltd.aiodu;

// Serializable 可序列化

import java.io.Serializable;

public class User implements Serializable {
    private int userid;
    private String username;
    private String userpassword;

    public void setUserid(int userid) {
        this.userid = userid;
    }

    public void setUsername(String username) {
        this.username = username;
    }

    public void setUserpassword(String userpassword) {
        this.userpassword = userpassword;
    }

    @Override
    public String toString() {
        return "User{" +
                "userid=" + userid +
                ", username='" + username + '\'' +
                ", userpassword='" + userpassword + '\'' +
                '}';
    }
}

```

### 用户接口(dao层)
```java
	// 用户持久层接口
	public interface IuserDao {
	    // 添加数据
	    int insertMall(User user);
	    // 删除数据
	    int deleteMall(User user);
	    // 修改数据
	    int updateMall(User user);
	    // 查询所有操作
	    List<User> findAll();
	}
```


### `MYSQL`数据库准备一张表
```sql
	mysql> select * from mall_info;
	+--------+-------------+--------------+
	| userid | username    | userpassword |
	+--------+-------------+--------------+
	|   1001 | user1001    | user1001     |
	|   1002 | user1002    | user1002     |
	|   1003 | user1003    | user1003     |
	|   1004 | user1004    | user1004     |
	|   1005 | user1005    | user1005     |
	|   1006 | user1006    | user1006     |
	|  12431 | user0012300 | user000000   |
	| 100000 | aidou       | user193161   |
	| 193162 | user193162  | user193162   |
	| 193163 | user000000  | user000000   |
	+--------+-------------+--------------+
	10 rows in set (0.00 sec
```
### Mapper(可随意更改`SQL`)：
```sql
	<mapper namespace="com.ltd.dao.IuserDao">
		<select id="findAll" resultType="com.ltd.aiodu.User">
		    -- 查询 mall 数据库下mall_info 表的所有信息 id = 方法名
		    select * from mall.mall_info;
		</select>

		<insert id="insertMal">
		    insert into mall.mall_info values(12431,'user0012300','user000000');
		</insert>
		    
	    <delete id="deleteMall">
	        delete from mall.mall_info where userid="12431"
	    </delete>
	
	    <update id="updateMal">
	        update mall.mall_info set userid='100000' where userid=0;
	    </update>
</mapper>
```


### 实现测试方法:
```java

public class MybatisTest {
    SqlSession session = null;
    @Before
    public void testBefore() throws IOException {
        InputStream in = Resources.getResourceAsStream("SqlMapConfig.xml");
        SqlSessionFactoryBuilder builder = new SqlSessionFactoryBuilder();
        SqlSessionFactory factory = builder.build(in);
        session = factory.openSession(true); // true 自动提交，默认 false ，也可手动提交 -- session.commit(); 
    }

    // 新形势数据的插
    @Test
    public void insertMalls() {
        // 添加一条数据 000000 user000000 user000000
        // 通过 session 执行 sql 语句，返回执行结果
        int rows = session.insert("com.ltd.dao.IuserDao.insertMal");
        System.out.println("影响的行数: " + rows);
    }

    // 数据的删除
    @Test
    public void delete() {
        int rows = session.delete("com.ltd.dao.IuserDao.deleteMall");
        System.out.println("删除影响的行数: " + rows);
    }

    // 数据的更改
    @Test
    public void update() {
        int nums = session.update("com.ltd.dao.IuserDao.updateMal");
        System.out.println("更新影响的行数: " + nums);
    }
   
   // 数据查询
  @Test
    public void findAll(){
       List<User> users = session.selectList("com.ltd.dao.IuserDao.findAll");
       for(User user:users){
           System.out.println(user);
       }
    }
}

```