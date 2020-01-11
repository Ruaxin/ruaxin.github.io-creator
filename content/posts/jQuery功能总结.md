---
title: "jQuery功能总结"
date: 2019-11-28T17:26:34+08:00
draft: false
---

# jQuery功能总结

## 1.jQuery 如何获取元素

jQuery()描述: 接受一个包含一个CSS选择器的字符串，用于匹配的一组元素。  
关于如何获取元素，jQuery是这样做的，我们将一个选择表达式，放进构造函数jQuery()（简写为$），然后就能得到被选中的元素。
{{< highlight js>}}
　　$(document) //选择整个文档对象

　　$('#myId') //选择ID为myId的网页元素

　　$('div.myClass') // 选择class为myClass的div元素

　　$('input[name=first]') // 选择name属性等于first的input元素
{{< / highlight >}}

## 2.jQuery 的链式操作是怎样的

关于链式操作，我们先来看代码：
{{< highlight js>}}
　$('#test').find('.red').addClass("blue")
{{< / highlight >}}

如代码所见，链式操作就是选中网页元素以后，可以对它进行一系列操作，并且所有操作可以连接在一起，以链条的形式写出来。  
之所以能这么操作，是因为return this之后，返回了当前调用的这个方法的实例对象this，那就可以继续访问自己的原型了。例：
{{< highlight js>}}
  addClass(className) {
    for (let i = 0; i < this.elements.length; i++) {
      const element = this.elements[i]
      element.classList.add(className)
    }
    return this
  }
{{< / highlight >}}

## 3.jQuery 如何创建元素

还是先看源码：
{{< highlight js>}}
  let elements
  if (typeof selectorOrArrayOrTemplate === "string") {
    if (selectorOrArrayOrTemplate[0] === "<") {
      // 创建 div
      elements = [createElement(selectorOrArrayOrTemplate)]
    } else {
      // 查找 div
      elements = document.querySelectorAll(selectorOrArrayOrTemplate)
    }
  } else if (selectorOrArrayOrTemplate instanceof Array) {
    elements = selectorOrArrayOrTemplate
  }
{{< / highlight >}}
所以创建元素的方法还是用$()，只要把新元素直接传入jQuery的构造函数就行了，它会通过对'<'的判断，自动选择查找还是创建：
{{< highlight js>}}
　　$('<p>Hello</p>')

　　$('<li class="new">new list item</li>')

　　$('ul').append('<li>list item</li>')

{{< / highlight >}}
## 4.jQuery 如何移动元素

关于移动，有两种方法，一种方法是直接移动该元素，另一种方法是移动其他元素。  
比如使用.insertAfter()，把div元素移动p元素后面：
{{< highlight js>}}
　$('div').insertAfter($('p'))
{{< / highlight >}}
或者使用.after()，把p元素加到div元素前面：
{{< highlight js>}}
　$('p').after($('div'));
{{< / highlight >}}
表面上看，这两种方法对于移动的效果是一样的。但是实际上，返回的元素不一样。第一种方法返回div元素，第二种方法返回p元素，这就会影响你之后的链式操作。  
使用这种模式的操作方法，一共有四对：  
{{< highlight js>}}
　　.insertAfter().after()//在现存元素的外部，从后面插入元素

　　.insertBefore().before()//在现存元素的外部，从前面插入元素

　　.appendTo().append()//在现存元素的内部，从后面插入元素

　　.prependTo().prepend()//在现存元素的内部，从前面插入元素
{{< / highlight >}}
## 5.jQuery 如何修改元素的属性

常用的一些修改元素属性的API
{{< highlight js>}}
  .addClass() //为每个匹配的元素添加指定的样式类名               
  .html() //取出或设置html内容
  .text() //取出或设置text内容
  .attr() //取出或设置某个属性的值
  .width() //取出或设置某个元素的宽度
  .height() //取出或设置某个元素的高度
  .val() //取出某个表单元素的值
{{< / highlight >}}

**资料来源1：http://www.ruanyifeng.com/blog/2011/07/jquery_fundamentals.html**  
**资料来源2：https://www.jquery123.com/**
