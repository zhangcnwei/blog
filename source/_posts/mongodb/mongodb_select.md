---
title: mongoDB 条件查询
date: 2016-2-12
reward: true
tags: 
    - DB
    - mongoDB
---

1. 条件操作符

   "$lt"    =>  "<"

   "$lte"  =>  "<="

   "$gt"   =>  ">"

   "$gte" =>  ">="

   "$ne"  =>  "!="

   例 1: 某集合B集合中文档有属性x值为整数，需查找10<x<=30的文档  

   > db.B.find({"x":{"$gt":10,"$lte":30}});

   例 2: 从某集合B中查找日期属性day值大于2012/01/01的文档数据

   > db.B.find({"day":{"$gt":new Date("2012/01/01")}})

2. $in包含/$nin不包含

   $in : 查询匹配指定条件值的文档；

   $nin ：查询不匹配指定条件值的文档；

   > db.B.find({"x":{"$in":['值1','值2',.....]}})
   >
   > db.B.find({"x":{"$nin":['值1','值2',.....]}})

3. $or或查询

   $or:查询匹配多个条件多个值的文档；

   > db.B.find({"$or":[{"x":{"$in":['值1','值2'...]}},{"y":"3"}]})

4. $all匹配所有

   比如文档：

   {"name":jack,"age":[1,2,3]}

   {"name":jack,"age":[1,4,3]}

   > db.B.find({"age":{"$all":[2,3]}})

​       结果：{"name":jack,"age":[1,2,3]}

5. $exists 判断文档属性是否存在

   > db.B.find({"name":{"$exists":true}})   --查找属性name存在的文档
   >
   > db.B.find({"name":{"$exists":false}})  --查找属性name不存在的文档

6. 属性值为null情况

   如下操作并可知道：

   > db.C.find()

   { "_id" : ObjectId("5018fccd1781352fe25bf511"), "a" : "14", "b" : "14" }

   { "_id" : ObjectId("5018fccd1781352fe25bf512"), "a" : "15", "b" : "15" }

   { "_id" : ObjectId("5018fccd1781352fe25bf510"), "a" : "13", "b" : "13", "c" : null }

   > db.C.find({"c":null})

   { "_id" : ObjectId("5018fccd1781352fe25bf511"), "a" : "14", "b" : "14" }

   { "_id" : ObjectId("5018fccd1781352fe25bf512"), "a" : "15", "b" : "15" }

   { "_id" : ObjectId("5018fccd1781352fe25bf510"), "a" : "13", "b" : "13", "c" : null }

   可见查询属性c值为null文档，包括属性c值为null、该属性c不存在两个部分。若想只查询属性c为null的文档

   如下：

   > db.C.find({"c":{"$in":[null],"$exists":true}})

   { "_id" : ObjectId("5018fccd1781352fe25bf510"), "a" : "13", "b" : "13", "c" : null }

   ​

7. $mod取模运算, $not元条件句

   db.B.find({"age":{"$mod":[5,1]}}) --表示查找年龄/5余1的所有文档

   若查找年龄/5余1之外的所有文档，可结合$not运算：

   db.B.find({"age":{"$not":{"$mod":[5,1]}}})

   例：

   > db.tianyc02.find({age:{$mod:[11,0]}})

   { "_id" : ObjectId("50ea6b6f12729d90ce6e341b"), "name" : "xtt", "age" : 11 }

   { "_id" : ObjectId("50ea6b7312729d90ce6e341c"), "name" : "xtt", "age" : 22 }

   > db.tianyc02.find({age:{$not:{$mod:[11,0]}}})

   { "_id" : ObjectId("50ea6eba12729d90ce6e3423"), "name" : "xttt", "age" : 111 }

   { "_id" : ObjectId("50ea6eba12729d90ce6e3424"), "name" : "xttt", "age" : 222 }

   $mod会将查询的值除以第一个给定的值，若余数等于第二个给定的值，则返回该结果。

   $not与正则表达式联合使用时极为有效，用来查找那些与特定模式不匹配的文档。

   ​

8. 正则表达式

   > db.B.find({"name":/jack/i})

9. $size

   > db.C.find()

   { "_id" : ObjectId("501e71557d4bd700257d8a41"), "a" : "1", "b" : [ 1, 2, 3 ] }

   { "_id" : ObjectId("501e71607d4bd700257d8a42"), "a" : "1", "b" : [ 1, 2 ] }

   > db.C.find({"b":{"$size":2}})

   { "_id" : ObjectId("501e71607d4bd700257d8a42"), "a" : "1", "b" : [ 1, 2 ] }

   ​

10. $slice

    返回数组的一个子集，即对以某属性为基础，返回多少条（范围）。也可以接受偏移值和要返回的元素数量，来返回中间的结果。

    > db.C.find()

    { "_id" : ObjectId("501e71557d4bd700257d8a41"), "a" : "1", "b" : [ 1, 2, 3 ] }

    { "_id" : ObjectId("501e71607d4bd700257d8a42"), "a" : "1", "b" : [ 1, 2 ] }

    > db.C.findOne({},{"b":{"$slice":[2,3]}})

    { "_id" : ObjectId("501e71557d4bd700257d8a41"), "a" : "1", "b" : [ 3 ] }

    > db.C.findOne({},{"b":{"$slice":-2}})

    {"_id" : ObjectId("501e71557d4bd700257d8a41"), "a" : "1", "b" : [ 2, 3 ]}

    ​

11.  $where

    即可执行任务javascript作为查询的一部分。

    $where的值可以是function、也可以是字符串等等。

    db.C.find({"$where":function(){return this.a == "1"}}) 与 db.C.find({"$where":"this.a == '1'"}})

    注意：采用$where子句查询在速度上较常规查询慢的多。因文档需要从BSON转换成javascript对象，然后通过"$where"的表达式来运行。
    
    不用利用索引。可用常规查询做前置过滤，配置"$where"查询进行调优，可达到不牺牲性能的要求。