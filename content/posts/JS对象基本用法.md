---
title: "JS对象基本用法"
date: 2019-11-10T12:05:40+08:00
draft: false
---

# JS对象基本用法

## 1 声明对象的两种语法

写法1：
```
let obj = {'name': 'frank', 'age': 18}
```
写法2：
```
let obj = new Objext({'name': 'frank'})
```
细节：  
- 键名是字符串，不是标识符，可以包括任意字符
- 引号可省略，省略之后就只能写标识符
- 就算引号省略了，键名也还是字符串  

## 2 如何删除对象的属性

写法1：
```
delete obj.xxx
```
写法2：
```
delete obj['xxx']
```

## 3 如何查看对象的属性

### 1.查看自身所有属性
```
Object.keys(obj)
```
### 2.查看自身所有属性的值
```
Object.values(obj)
```
### 3.查看自身所有属性和值
```
Object.entries(obj)
```
### 4.查看自身+共有属性  
写法1：
```
console.dir(obj)
```
写法2：
```
obj.__proto__
```
### 5.两种方法查看单个属性
中括号语法：
```
obj['key']
```
点语法：
```
obj.key
```

**重点**  
```obj.name```等价于```obj['name']```  
```obj.name```不等价于```obj[name]```  
name是字符串，而不是变量

## 4 如何修改或增加对象的属性
### 1.直接赋值
```
let obj = {name: 'frank'}
obj.name = 'frank'
obj['name'] = 'frank'
obj['na' + 'me'] = 'frank'
let key = 'name';obj[key] = 'frank'
```
### 2.批量赋值
```
Object.assign(obj, {age:18,gender:'nam'})
```
### 3.共有属性的修改法
```
let common = {kind:'human'}
let obj = Object.create(common)
```

## 5 'name' in obj和obj.hasOwnProperty('name') 的区别
判断是否有这个属性是用
```
'name' in obj
```
判断一个属性是自身的还是共有的用
```
obj.hasOwnProperty('name')
```

**资料来源：饥人谷**