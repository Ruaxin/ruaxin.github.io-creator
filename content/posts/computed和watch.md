---
title: "computed和watch"
date: 2020-01-11T12:53:50+08:00
draft: false
---
# computed
计算属性：  

* 从其他属性计算而来的属性变成一个属性,调用时不需要加括号。 
* 会根据依赖数据发生的改变，进行计算，显示新的结果，这个结果支持缓存，所以只有当依赖的数据改变时，才会重新计算.  
* 不支持异步，当computed内有异步操作时无效，无法监听数据的变化.  
* 计算属性将被混入到 Vue 实例中。所有 getter 和 setter 的 this 上下文自动地绑定为 Vue 实例。  
 
{{< highlight js>}}
var vm = new Vue({
  data: { a: 1 },
  computed: {
    // 仅读取
    aDouble: function () {
      return this.a * 2
    },
    // 读取和设置
    aPlus: {
      get: function () {
        return this.a + 1
      },
      set: function (v) {
        this.a = v - 1
      }
    }
  }
})
vm.aPlus   // => 2(不需要加括号)
vm.aPlus = 3
vm.a       // => 2
vm.aDouble // => 4
{{< / highlight >}}

# watch
监听：  

* 一个对象，键是需要观察的表达式，值是对应回调函数。值也可以是方法名，或者包含选项的对象。Vue 实例将会在实例化时调用 $watch()，遍历 watch 对象的每一个属性。
* 当一个属性发生变化时，就会执行对应的操作。
* 监听的函数接收两个参数，第一个参数是最新的值；第二个参数是输入之前的值。
* deep：是否监听里面的属性
* immediate：是否在第一次渲染时要执行
* 不支持缓存,但支持异步

{{< highlight js>}}
var vm = new Vue({
  data: {
    a: 1,
    b: 2,
    c: 3,
    d: 4,
    e: {
      f: {
        g: 5
      }
    }
  },
  watch: {
    a: function (val, oldVal) {
      console.log('new: %s, old: %s', val, oldVal)
    },
    // 方法名
    b: 'someMethod',
    // 该回调会在任何被侦听的对象的 property 改变时被调用，不论其被嵌套多深
    c: {
      handler: function (val, oldVal) { /* ... */ },
      deep: true
    },
    // 该回调将会在侦听开始之后被立即调用
    d: {
      handler: 'someMethod',
      immediate: true
    },
    e: [
      'handle1',
      function handle2 (val, oldVal) { /* ... */ },
      {
        handler: function handle3 (val, oldVal) { /* ... */ },
        /* ... */
      }
    ],
    // watch vm.e.f's value: {g: 5}
    'e.f': function (val, oldVal) { /* ... */ }
  }
})
vm.a = 2 // => new: 2, old: 1
{{< / highlight >}}
