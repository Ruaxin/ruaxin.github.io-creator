---
title: "浅析Vue"
date: 2020-01-07T17:32:37+08:00
draft: false
---

## Vue的两个版本
1. 完整版vue.js 
* 完整版：同时包含编译器和运行时的版本。
* 编译器：用来将模板字符串编译成为 JavaScript 渲染函数的代码。
2. 只包含运行时版vue.runtime.js
* 运行时：用来创建 Vue 实例、渲染并处理虚拟 DOM 等的代码。基本上就是除去编译器的其它一切。
* 因为运行时版本相比完整版体积要小大约 30%，所以应该尽可能使用这个版本。

***
|              | Vue完整版                      | Vue非完整版                   |
| ------------ | ------------------------------ | ----------------------------- |
| 特点         | 有compiler                     | 没有compiler                  |
| 视图         | 写造HTML里或者写在template选项 | 写在render函数里用h来创建标签 |
| cdn引入      | vue.js                         | vue.runtime.js                |
| webpack引入  | 需要配置alias                  | 默认使用此版                  |
| @vue/cli引入 | 需要额外配置                   | 默认使用此版                  |
***

## template 和 render

* template：一个字符串模板作为 Vue 实例的标识使用。模板将会 替换 挂载的元素。挂载元素的内容都将被忽略，除非模板的内容有分发插槽。如果值以 # 开始，则它将被用作选择符，并使用匹配元素的 innerHTML 作为模板。
* render：字符串模板的代替方案，允许你发挥 JavaScript 最大的编程能力。该渲染函数接收一个 createElement 方法作为第一个参数用来创建 VNode。如果组件是一个函数组件，渲染函数还会接收一个额外的 context 参数，为没有实例的函数组件提供上下文信息。Vue 选项中的 render 函数若存在，则 Vue 构造函数不会从 template 选项或通过 el 选项指定的挂载元素中提取出的 HTML 模板编译渲染函数。

```
// 需要编译器
new Vue({
  template: '<div>{{ hi }}</div>'
})

// 不需要编译器
new Vue({
  render (h) {
    return h('div', this.hi)
  }
})
```

## 补充（在线预览Vue项目）

登入codesandbox.io，点击create a sandbox，选择vue，就能创建Vue项目，实现在线预览了。如果需要下载项目，在File中选择Export to ZIP就能下载。
