---
title: PyMYSQL CURD
tags: SQL
categories: SQL
cover: 'https://gitee.com/wang_hong_bin/pic-go-photos/raw/master/Pymysql.jpg'
abbrlink: 243
date: 2020-10-13 19:15:41
top_img:
---

```sql
-- 存在一条问题:

-- userinfo 表的数据通过循环读取到多条暂未解决

-- 此环境下只保留一条数据 用作模拟登陆

mysql> desc userinfo;
+----------+-------------+------+-----+---------+-------+
| Field    | Type        | Null | Key | Default | Extra |
+----------+-------------+------+-----+---------+-------+
| username | varchar(16) | NO   | PRI | NULL    |       |
| password | int(18)     | NO   |     | NULL    |       |
+----------+-------------+------+-----+---------+-------+
2 rows in set (0.02 sec)

-- 表 user_id 用来存放 OEM 的增删改查的数据

mysql> desc user_id;
+-----------+-------------+------+-----+---------+-------+
| Field     | Type        | Null | Key | Default | Extra |
+-----------+-------------+------+-----+---------+-------+
| id        | int(12)     | NO   | PRI | 0       |       |
| user_name | char(9)     | YES  |     | NULL    |       |
| gender    | char(6)     | YES  |     | NULL    |       |
| address   | varchar(18) | YES  |     | NULL    |       |
+-----------+-------------+------+-----+---------+-------+
4 rows in set (0.02 sec)

-- 中文字符集乱码问题:

-- 输入如下 命令解决中文乱码

mysql> set character_set_results=gb2312;

```

```python
 import pymysql  # 导入第三方模块 pymysql 库


class Oper_Sql:
    select_user_login = 'select username,password from userinfo'  # 查询 登录信息语句

    select_user_info = 'select id,user_name,gender,address from user_id'  # 查询表的数据信息

    select_self_value = 'select id,user_name,gender,address from user_id where id = %s'  # 精准查询根据输入 id 时查询


count = 3
while count >= 1:
    def main():
        try:
            ''' 异常  '''
            # 1. 创建连接对象

            conn = pymysql.connect(host='localhost',
                                   password='root',
                                   user='root',
                                   charset='utf8',
                                   port=3306,
                                   db='scott',
                                   cursorclass=pymysql.cursors.DictCursor  # 改变为字典对象
                                   )
            print(conn)  # 打印连接对象地址代表成功

            # 序号 1 执行查询操作
            def select_user():
                '''  序号 1 查询操作 '''
                # 查询sql
                try:
                    with conn.cursor() as cursor:
                        cursor.execute(Oper_Sql.select_user_info)  # 查询 user_id 表
                        table_name = input('请输入您查询表的名称: ')

                        # 循环遍历表 user_id
                        for user_i in cursor.fetchall():
                            # 判断表为空的条件
                            id = user_i['id']
                            name = user_i['user_name']
                            gender = user_i['gender']
                            address = user_i['address']

                            print('''
                                    ------------------------------
                                              查询 {} 表
                                    ID: {}
                                    Name: {}
                                    Gendegr: {}
                                    Address: {}
                                    -----------------------------
                                    '''.format(table_name, id, name, gender, address))
                except Exception as err:
                    print('登陆后查询时异常: ', err)
                # 调用查询结束  # # #

            # 序号 2 执行 准确信息查询 比如根据 id 或者 name 查询
            def select_self():
                try:
                    with conn.cursor() as cursor:
                        self_value = input('请输入您要查询的编号: ')
                        cursor.execute(query=Oper_Sql.select_self_value, args=[self_value])
                        for self_all in cursor.fetchall():
                            id = self_all['id']
                            name = self_all['user_name']
                            gender = self_all['gender']
                            address = self_all['address']
                            print('''
                            -----------------------------------------------------------------
                            
                            精准查询的结果为:
                            
                            ID: {}\tName: {}\tGender: {}\tAddress: {}
                            
                            -----------------------------------------------------------------
                            '''.format(id, name, gender, address))

                except Exception as err:
                    print('精准查询时的异常: ', err)

            # 通过键盘输入特定字段并进行数据库数据源的更新
            def update_user_info():
                try:
                    with conn.cursor() as cursor:

                        # 根据输入完成更新操作
                        set_column_name = input('请输入字段名[set id =""]: ')  #
                        new_value = input('请输入修改的新值: ')
                        column_name = input('请输入字段名[set id =""]: ')
                        where_column_name = input('请输入依据的条件字段名[where ="193161"]: ')

                        # 动态输入字段及更新的新值
                        cursor.execute('update user_id set %s = %s where %s = %s ' % (
                            str(set_column_name), new_value, column_name, where_column_name))
                        # 提交事务
                        conn.commit()
                        print('更新成功,结果: {} : {} '.format(set_column_name, new_value))

                except Exception as err:
                    print('修改数据时的异常: ', err)

            # 删除用户个人信息
            def delete_self_info():
                try:
                    with conn.cursor() as cursor:
                        delete_table_name = input('请输入您要删除数据的表: ')
                        delete_con = input('请输入条件字段名: ')  # conditions 条件
                        delete_con_value = input('请输入删除条件的值: ')
                        # 删除的 SQL 语句
                        cursor.execute(
                            'delete from %s where %s = %s' % (delete_table_name, delete_con, delete_con_value))
                        conn.commit()
                        print('在表: {} 中根据 {} = {} 的记录已经被成功删除!'.format(delete_table_name, delete_con, delete_con_value))
                except Exception as err:
                    print('删除数据时的异常: ', err)

            # 插入用户信息
            def insert_self_info():
                try:
                    with conn.cursor() as cursor:
                        insert_id = input('请输入您的ID: ')
                        insert_name = input('请输入您的姓名: ')
                        insert_gender = input('请输入您的性别: ')
                        insert_address = input('请输入您的地址: ')
                        # MYSQL 列名重命名: alter table 表名 change column 列名 数据类型;

                        insert_self_value = "insert into user_id values(%s,%s,%s,%s)"
                        cursor.execute(query=insert_self_value,
                                       args=[insert_id, insert_name, insert_gender, insert_address])
                        for i in cursor.fetchall():
                            id = i['id']
                            user_name = i['user_name']
                            gender = i['gender']
                            address = i['address']

                        conn.commit()
                        print('在表 user_id 中成功插入ID: {}\tName: {}\tGender: {}\tAddress: {}'.format(id, user_name, gender,
                                                                                                 address))
                except Exception as err:
                    print('插入数据时的异常: ', err)

            def login():

                ''' 登录模块 '''

                with conn.cursor() as cursor:
                    cursor.execute(Oper_Sql.select_user_login)  # 执行查询语句
                    for user in cursor.fetchall():
                        username = user['username']
                        password = user['password']
                        # print(username,password) # 读取成功并追加到 列表中

                        # 创建空字典空列表，将username，password 存入字典 在将字典存在列表之后，将字典中的值取出与输入的值进行对比
                        user_info = []
                        user_dict = {}

                        # 字典赋值
                        user_dict['username'] = username
                        user_dict['password'] = password
                        # 追加列表到字典
                        user_info.append(user_dict)
                        print(user_info)
                        user = input('请输入您的用户名: ')
                        password = int(input('请输入您的密码: '))

                        if user_dict['username'] == user and user_dict['password'] == password:
                            print('数据库已经成功登录!')
                            # 进入管理系统 -- 执行一系列的操作
                            print('''
                                    ---------------------------------
                                    *        用户注册管理系统         *
                                    ----------------------------------
                                    +                                
                                    |    *1. 查询所有用户信息         
                                    +                               
                                    |    *2. 查找个人相关信息        
                                    +                              
                                    |    *3. 修改用户个人的信息      
                                    +                              
                                    |    *4. 删除用户个人信息         
                                    +                               
                                    |    *5. 添加新用户信息      
                                    +
                                    |    *6. 关闭数据库连接    
                                    ---------------------------------
    
                                    ''')
                            # select_user()
                            while True:
                                input_number = input('请输入您需要操作的编号[1~6]: ')

                                if input_number == '1':  # 输入编号 1 执行查询表操作
                                    select_user()
                                elif input_number == '2':  # 输入编号 2 执行精准信息查询
                                    select_self()
                                elif input_number == '3':
                                    update_user_info()
                                elif input_number == '4':
                                    delete_self_info()
                                elif input_number == '5':
                                    insert_self_info()
                                elif input_number == '6':
                                    close_oem = input('确定要关闭数据库连接 yes or no?: ')
                                    if close_oem == 'yes':
                                        print('欢迎使用OEM管理系统,再见!')
                                        break
                                else:
                                    print('请输入1~6之间的编号!')

                        else:
                            print('登陆失败!')

            # 调用登录
            login()



        # 1. 连接数据库成功后调用登录函数进行校验数据

        except Exception as err:
            print('连接时异常: ', err)  # 捕获异常错误进行输出
        finally:
            conn.close()
            conn.rollback() # 回滚的位置需要在考虑
		

    if __name__ == '__main__':
        main()  # 调用 main 方法
        print('剩余输入次数: ', count)
        count -= 1

```
+ 数据库连接成功后的部分截图
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200514163744392.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MzM0MDQyMA==,size_16,color_FFFFFF,t_70#pic_center)
+ 插入功能 `: 5`、查询实现`: 1`
![实现插入查询](https://img-blog.csdnimg.cn/2020051416412938.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MzM0MDQyMA==,size_16,color_FFFFFF,t_70#pic_center)