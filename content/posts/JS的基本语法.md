---
title: "JS的基本语法"
date: 2019-11-06T20:33:22+08:00
draft: false
---

# JS的基本语法
## 1. 表达式与语句
1. 表达式  
1+2表达式的**值**为3  
add(1,2)表达式的值为函数的**返回值**  
console.log表达式的值为**函数本身**  
console.log(3)表达式的值为undefined

2. 语句  
var a = 1 是一个语句

1. 二者的区别  
表达式一般都有值，语句可能有也可能没有  
语句一般会改变环境（声明、赋值）  
上面两句话并不是绝对的

4. 关于空格的补充  
大部分空格没有实际意义  
var a = 1和var a=1没有区别  
加回车大部分时候也不影响  
只有return后面不能加回车


## 2. 标识符
变量名就是是标识符。JS的标识符对大小写敏感，所以a和A是两个不同的标识符。  
规则：  
1. 第一个字符，可以是Unicode字母或$或_或中文  
2. 后面的字符，除了上面的，还可以有数字  
标识符错误示例：  
![BSF.png](https://i.loli.net/2019/11/06/8qPcxb2Kf5sjpCY.png)  

## 3. if else 语句
语法:
1. if(表达式){语句1}else{语句2}
2. {}可以在只有一句时省略  

代码示例：
{{< highlight js>}}
if (m === 3) {
  // 满足条件时，执行的语句
} else {
  // 不满足条件时，执行的语句
}
{{< / highlight >}}
**if else**(else代码块总是与离自己最近的那个if语句配对):
{{< highlight js>}}
if (m === 0) {
  // ...
} else if (m === 1) {
  // ...
} else if (m === 2) {
  // ...
} else {
  // ...
}
{{< / highlight >}}

## 4. while 和 for 语句
white 语法:  
1. white(表达式){语句}
2. 判断表达式的真假
3. 当表达式为真，执行语句
4. 当表达式为假，执行后面的语句
5. 执行完再次判断表达式的真假

代码示例：
{{< highlight js>}}
var i = 0;

while (i < 100) {
  console.log('i 当前为：' + i);
  i = i + 1;
}
{{< / highlight >}}
for 语法:  
1. for(语句1;表达式2;语句3){循环体}
2. 先执行语句1
3. 然后判断表达式2
4. 如果为真，执行循环体，然后执行语句3
5. 如果为假，直接退出循环，执行后面的语句

代码示例：
{{< highlight js>}}
vvar x = 3;
for (var i = 0; i < x; i++) {
  console.log(i);
}
{{< / highlight >}}
## 5. break 和 continue 语句

1. break语句用于跳出代码块或循环。(退出所有循环)
2. continue语句用于立即终止本轮循环，返回循环结构的头部，开始下一轮循环。(退出当前一次循环)

break示例：
{{< highlight js>}}
var i = 0;

while(i < 100) {
  console.log('i 当前为：' + i);
  i++;
  if (i === 10) break;
}
//上面代码只会执行10次循环，一旦i等于10，就会跳出循环
{{< / highlight >}}

continue示例：
{{< highlight js>}}
var i = 0;

while (i < 100){
  i++;
  if (i % 2 === 0) continue;
  console.log('i 当前为：' + i);
}
//上面代码只有在i为奇数时，才会输出i的值。如果i为偶数，则直接进入下一轮循环
{{< / highlight >}}

## 6. label
语法:
{{< highlight js>}}
foo: {
    console.log(1);
    break foo;
    console.log('这行不会输出')
}
console.log(2);
{{< / highlight >}}
面试考题：
{{< highlight js>}}
{
    foo: 1
}
{{< / highlight >}}
答：这并不是一个对象，这是一个标签，标签的内容是1。

## 7. switch语句
语法：
{{< highlight js>}}
switch (fruit) {
  case "banana":
    // ...
    break;
  case "apple":
    // ...
    break;
  default:
    // ...
}
{{< / highlight >}}
## 8. 其他简写语句
1. 问号冒号表达式  
表达式1?表达式2:表达式3
2. &&短路逻辑  
A&&B&&C&&D取第一个假值或D  
并不会取true/false
3. ||短路逻辑  
A||B||C||D取第一个真值或D  
并不会取true/false

关于&&的逻辑图：  
![BB.png](https://i.loli.net/2019/11/06/pcq8jsKtiEN4Dmo.png)
 
**资料来源：https://wangdoc.com/javascript/basic/grammar.html**