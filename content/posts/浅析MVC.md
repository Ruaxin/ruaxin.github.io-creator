---
title: "浅析MVC"
date: 2019-12-29T14:28:33+08:00
draft: false
---

# 什么是MVC

模型model用于封装与应用程序的业务逻辑相关的数据以及对数据的处理方法，会有一个或多个视图监听此模型。一旦模型的数据发生变化，模型将通知有关的视图。

视图view是它在屏幕上的表示，描绘的是model的当前状态。当模型的数据发生变化，视图相应地得到刷新自己的机会。

控制器controller定义用户界面对用户输入的响应方式，起到不同层面间的组织作用，用于控制应用程序的流程，它处理用户的行为和数据model上的改变。

M:数据相关都放到m
{{< highlight js>}}
const m = {
  data: {},//数据
  create(){},//增
  delete(){},//删
  update(){},//改
  get(){}//查
}
{{< / highlight >}}
V:视图相关都放到v
{{< highlight js>}}
const v = {
  el: ,//元素
  html: ``,//页面
  init(){},//初始化
  render(){}//更新
}
{{< / highlight >}}
C:控制器相关的都放在c
{{< highlight js>}}
const c = {
  events:{},//事件
  add(){},//方法
}
{{< / highlight >}}

# EventBus

eventBus 提供了 on、off 和 trigger 等 API，on 用于监听事件，trigger 用域触发事件。主要用于对象间通信,使用 eventBus 可以满足最小知识原则，m 和 v 互相不知道对方的细节，但是却可以调用对方的功能.
{{< highlight js>}}
const c = {
    eventBus.on('m:updated', () => {
        v.render(m.data.n)
        })//在控制器中监听v的更新事件
}
{{< / highlight >}}



# 表驱动编程

表驱动法是一种编程模式(scheme)——从表里面查找信息而不使用逻辑语句(if和case)。事实上，凡是能通过逻辑语句来选择的事物，都可以通过查表来选择。对简单的情况而言，使用逻辑语句更为容易和直白。但随着逻辑链的越来越发杂，查表法也就愈发显得更具吸引力。
比如：
{{< highlight js>}}
$button1.on("click", () => {
  let n;
  n += 1;
});
$button2.on("click", () => {
  let n;
  n -= 1;
});
{{< / highlight >}}
改成：
{{< highlight js>}}
events:{
    'click #add1': 'add',
    'click #minus1': 'minus'
  },
  add(){
    n + 1
  },
  minus(){
    n - 1
  }
{{< / highlight >}}
# 浅谈框架
MVC作为一种架构设计模式，它通过关注点分离鼓励改进应用程序组织。在它出现之后也一直在演变，有MVC，MVP，MVVM等等，每个框架都有自己的特性，这些都是在经典MVC基础上随着时代的发展、应用环境的变化衍变出来的。框架虽然是一个很有争议性的话题，但我们更应该去关注框架是否运行良好、灵活，不必拘泥于某种模式。花时间去构建一个健壮、具有良好设计、遵从关注点分离的项目比花时间去争论更有意义。
