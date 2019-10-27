---
title: "CSS知识总结"
date: 2019-10-25T07:28:48+08:00
draft: false
---

# CSS知识总结

## 1.浏览器渲染原理

1. 根据HTML构建HTML树（DOM）
2. 根据CSS构建CSS树（CSSOM）
3. 将两棵树合并成一棵渲染树（render tree）
4. Layout布局（文档流、盒模型、计算大小和位置）
5. Paint绘制（把边框颜色、文字颜色、阴影等画出来）
6. Compose合成（根据层叠关系展示画面）

![1.PNG](https://i.loli.net/2019/10/27/tFSH7KDAibWnUq4.png)

## 2.CSS 动画的两种做法

### 1.transform 

  * 四个常用功能  
    - 位移 translate  
    - 缩放 scale  
    - 选择 rotate  
    - 倾斜 skew

具体内容：https://developer.mozilla.org/zh-CN/docs/Web/CSS/transform

红心动画代码示例（transform）:
```
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
  <title>JS Bin</title>
</head>
<body>
  <div id="heart">
    <div class="left"></div>
    <div class="right"></div>
    <div class="bottom"></div>
  </div>
</body>
</html>
```
```
* {
  box-sizing: border-box;
}
#heart {
  display: inline-block;
  margin: 100px;
  position: relative;
  transition: all 1s;
}
#heart:hover {
  transform: scale(1.2);
}
#heart>.left {
  background: red;
  width: 50px;
  height: 50px;
  position: absolute;
  transform: rotate(45deg) translateX(31px);
  bottom: 50px;
  left: -50px;
  border-radius: 50% 0 0 50%;
}
#heart>.right {
  background: red;
  width: 50px;
  height: 50px;
  border-radius: 50%;
  position: absolute;
  transform: rotate(45deg) translateY(31px);
  bottom: 50px;
  right: -50px;
  border-radius: 50% 50% 0 0;
}
#heart>.bottom {
  background: red;
  width: 50px;
  height: 50px;
  transform: rotate(45deg);
}
```
### 2.animation

* 缩写语法
  animation：时长|过渡方式|延迟|次数|方向|填充模式|是否暂停|动画名

  - 时长：1s或者1000ms
  - 过渡方式：跟transition取值一样，如linear
  - 次数：3或者2.4或者infinite
  - 方向：reverse|alternate|alternate-reverse
  - 填充模式：none|forwards|backwards|both
  - 是否暂停：paused|running
  
具体内容：https://developer.mozilla.org/zh-CN/docs/Web/CSS/animation

红心动画代码示例（animation）:
```
<!DOCTYPE html>
<html>

<head>
  <meta charset="utf-8">
  <title>JS Bin</title>
</head>

<body>
  <div id="heart">
    <div class="left"></div>
    <div class="right"></div>
    <div class="bottom"></div>
  </div>
</body>

</html>
```
```
* {
  box-sizing: border-box;
}
#heart {
  display: inline-block;
  margin: 100px;
  position: relative;
  animation: .5s heart infinite alternate-reverse;
}
@keyframes heart {
  0% {
    transform: scale(1);
  }
  100% {
    transform: scale(1.2);
  }
}
#heart>.left {
  background: red;
  width: 50px;
  height: 50px;
  position: absolute;
  transform: rotate(45deg) translateX(41px);
  bottom: 50px;
  left: -50px;
  border-radius: 50% 0 0 50%;
}
#heart>.right {
  background: red;
  width: 50px;
  height: 50px;
  border-radius: 50%;
  position: absolute;
  transform: rotate(45deg) translateY(41px);
  bottom: 50px;
  right: -50px;
  border-radius: 50% 50% 0 0;
}
#heart>.bottom {
  background: red;
  width: 50px;
  height: 50px;
  transform: rotate(45deg);
}
```

## 3.CSS动画优化

1. 看Google技术文章https://developers.google.com/web/fundamentals/performance/rendering/stick-to-compositor-only-properties-and-manage-layer-count
2. 使用requestAnimationFrame代替setTimeout或者setInterval
3. 使用will-change或translate

## 4.更新样式
![2.PNG](https://i.loli.net/2019/10/27/Nkn5IsWHfmDdyoY.png)