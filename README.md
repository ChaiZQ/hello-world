# -*- coding: utf-8 -*-
"""
Created on Thu Dec 28 16:08:46 2017

@author: Administrator
"""

import pymysql
# 创建连接，指定数据库的ip地址，账号、密码、端口号、要操作的数据库、字符集
conn = pymysql.connect(host='127.0.0.1', port=3306, user='root', passwd='mcfzsh', db='sci',charset='utf8')
# 创建游标
cursor = conn.cursor()
## 执行SQL，并返回收影响行数
#effect_row = cursor.execute("update table1 set data = '14/7/7' where id = 1;")
## 执行SQL，并返回受影响行数
##effect_row = cursor.execute("update students set name = 'niuhy' where id = %s;", (1,))
## 执行SQL，并返回受影响行数
#effect_row = cursor.executemany("insert into students (name,age) values (%s,%s); ", [("andashu",18),("12345",20)])
##执行select语句
#cursor.execute("SELECT * FROM sci.沪深ａ股20180103 where 代码=000001;")
cursor.execute("SELECT * FROM sci.sci_test where 期刊名称='Optics and Lasers in Engineering';")
sample1=cursor.fetchone()
print(sample1)

cursor.execute("select * from sci_test;")
#获取查询结果的第一条数据，返回的是一个元组
#row_1 = cursor.fetchone()
#print(row_1)
# 获取前n行数据
n=3
row_n = cursor.fetchmany(n)
print(row_n)
# 获取所有数据
row_3 = cursor.fetchall()
# 提交，不然无法保存新建或者修改的数据
conn.commit()
# 获取最新自增ID
new_id = cursor.lastrowid    

# 关闭游标
cursor.close()
# 关闭连接
conn.close()
 
 
 
##2.创建数据库表
#import pymysql
# 
#db = pymysql.connect("127.0.0.1", "root", "sunck", "kaige")
#cursor = db.cursor()
# 
## 检查表是否存在，如果存则删除
#cursor.execute("drop table if exists bandcard")
##建表
#sql = 'create table bandcard(id int auto_increment primary key, money int not null)'
#cursor.execute(sql)
# 
# 
#cursor.close()
#db.close()
# 
# 
# 
##3.数据库插入数据
#import pymysql
# 
#db = pymysql.connect("127.0.0.1", "root", "sunck", "kaige")
#cursor = db.cursor()
# 
# 
# 
#sql = 'insert into bandcard values(0, 300),(0, 400),(0, 500),(0, 600),(0, 700)'
#try:
#    cursor.execute(sql)
#    db.commit()
#except:
#    # 如果提交失败，回滚到上一次数据
#    db.rollback()
# 
# 
#cursor.close()
#db.close()
# 
# 
# 
##4.数据库更新操作
#import pymysql
# 
#db = pymysql.connect("127.0.0.1", "root", "sunck", "kaige")
#cursor = db.cursor()
# 
# 
# 
#sql = 'update bandcard set money=1000 where id=1'
#try:
#    cursor.execute(sql)
#    db.commit()
#except:
#    # 如果提交失败，回滚到上一次数据
#    db.rollback()
# 
# 
#cursor.close()
#db.close()
# 
# 
# 
##5数据库删除操作
#import pymysql
# 
#db = pymysql.connect("127.0.0.1", "root", "sunck", "kaige")
#cursor = db.cursor()
# 
## 检查表是否存在，如果存则删除
#cursor.execute("drop table if exists bandcard")
##建表
#sql = 'create table bandcard(id int auto_increment primary key, money int not null)'
#cursor.execute(sql)
# 
# 
#cursor.close()
#db.close()
# 
# 
# 
##数据库查询操作
#'''
#fetchone()
#功能：获取下一个查询结果集，结果集是一个对象
# 
#fetchall()
#功能：接收全部的返回的行
# 
#rowcount:是一个只读属性，返回execute()方法影响的行数
# 
#'''
#import pymysql
# 
#db = pymysql.connect("127.0.0.1", "root", "sunck", "kaige")
#cursor = db.cursor()
# 
# 
# 
#sql = 'select * from bandcard where money>400'
#try:
#    cursor.execute(sql)
# 
#    reslist = cursor.fetchall()
#    for row in reslist:
#        print("%d--%d" % (row[0], row[1]))
# 
#except:
#    # 如果提交失败，回滚到上一次数据
#    db.rollback()
#    
#cursor.close()
#db.close()
