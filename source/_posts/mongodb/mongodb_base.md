---
title: mongoDB 常用命令
date: 2016-2-08
reward: true
tags: 
    - DB
    - mongoDB
---

1. Help查看命令提示  
   `help;`                     
   `db.help(); `               
   `db.yourColl.help(); `   
   `db.youColl.find().help();`  
   `rs.help();`
    
2. 切换/创建数据库  
   `use yourDB;`  
   当创建一个集合(table)的时候会自动创建当前数据库
	 
3. 查询所有数据库  
   `show dbs;`
	 
4. 删除当前使用数据库  
   `db.dropDatabase();` 
   
5. 从指定主机上克隆数据库  
   `db.cloneDatabase(“127.0.0.1”);`
   > 将指定机器上的数据库的数据克隆到当前数据库

6. 从指定的机器上复制指定数据库数据到某个数据库  
   `db.copyDatabase("mydb", "temp", "127.0.0.1");` 
   > 将本机的mydb的数据复制到temp数据库中  
   
7. 修复当前数据库  
   `db.repairDatabase();`

8. 查看当前使用的数据库  
   `db.getName();
   db`
   > db和getName方法是一样的效果，都可以查询当前使用的数据库

9. 显示当前db状态  
   `db.stats();`
   
10. 当前db版本  
   `db.version();` 
   
11. 查看当前db的链接机器地址  
   `db.getMongo();`
