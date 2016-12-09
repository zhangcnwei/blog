---
title: angular 1.X 常用指令、函数
date: 2016-3-08
reward: true
tags: 
    - javascript
    - angular
---

## AngularJS指令

|指令|描述|说明|
| --------- |:-------------------------------------------:| -------:|
|ng-app|定义一个application的根元素|指令|
|ng-bind|将html元素的innerHTML绑定到application data|数据绑定|
|ng-click|定义html元素的click事件|绑定点击事件|
|ng-controller|定义一个application的控制对象|控制器|
|ng-disable|绑定application data到HTML元素的disabled属性|DOM节点|
|ng-hide|显示或隐藏HTML元素|DOM节点|
|ng-show|显示或隐藏HTML元素|DOM节点|
|ng-include|当前节点引用application中包含的HTML文件|Include|
|ng-init|定义一个application的初始值|指令|
|ng-model|双向绑定application data|指令|
|ng-repeat|为集合中的每一个数据项重复创建一段HTML元素|指令|

## 过滤器

|过滤器|描述|
| ------- | :----------------------------------------------: |
|currency|将数字格式化为现金格式|
|filter|从一个集合中选择子项|
|lowercase|将字符串转换为小写形式|
|uppercase|将字符串转换为大写形式|
|orderBy|通过一个表达式对集合元素进行排序|

## 数据比较

|方法|描述|
| ---------------- | :--------------------------------------------: |
|angular.isArray()|判断给定对象是否为数组|
|angular.isDate()|判断给定对象是否为日期类型|
|angular.isDefined()|判断给定对象是否为定义过|
|angular.isElement()|判断给定对象是否为一个DOM对象|
|angular.isFunction()|判断给定对象是否为函数|
|angular.isNumber()|判断给定对象是否为数子|
|angular.isObject()|判断给定对象是否为Object类型|
|angular.isString()|判断给定对象是否为字符串|
|angular.isUndefined()|判断给定对象是否没有定义过（与angular.isDefined()相反）|
|angular.isequals()|判断给定的两个对象是否相等|

## 数据转换

|方法|描述|
| ---------------- | :--------------------------------------------: |
|angular.lowercase()|将字符串转换为小写形式|
|angular.uppercase()|将字符串转换为大写形式|
|angular.copy()|深拷贝一个对象或数组|


## JSON相关

|方法|描述|
| ---------------- | :--------------------------------------------: |
|angular.fromJSON()|将给定的JSON对象反序列化为字符串|
|angular.toJSON()|将给定的字符串序列化为JSON对象|

## 基本API

|方法|描述|
| ---------------- | :--------------------------------------------: |
|angular.bootstarp()|手动引导AngularJS应用程序|
|angular.element()|将一个HTML元素包装成一个JQuery元素（然后你可以对它使用JQuery提供的方法）|
|angular.module()|创建，注册或重新恢复一个AngularJS模块|
|angular.forEach()|遍历对象或数组中的每一个元素并执行一个函数|

## 输入验证

|属性|描述|
| ---------------- | :--------------------------------------------: |
|$dirty|表示当前field中的内容被修改过|
|$valid|表示当前field中的内容是有效的|
|$invalid|表示当前field中的内容是无效的|
|$pristine|表示当前field中的内容还没被修改过|

