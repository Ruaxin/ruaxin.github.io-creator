---
title: "JS函数的执行时机"
date: 2019-11-12T21:50:29+08:00
draft: false
---

# JS函数的执行时机

先来看以下的这段代码
{{< highlight js>}}
let i = 0
for(i = 0; i<6; i++){
  setTimeout(()=>{
    console.log(i)
  },0)
}//结果会打印出6个6
{{< / highlight >}}
接下来解释一下为什么会打印出6个6：  
由于在执行setTimeout之前，先会完成for循环，并且因为i是在外面定义的，所以for循环里只有一个i。完成循环后，i的值为6，再之后执行6次setTimeout，最终打印出6个6。

---

如果把代码改成这样，就能打印出0,1,2,3,4,5
{{< highlight js>}}
for(let i = 0; i<6; i++){
  setTimeout(()=>{
    console.log(i)
  },0)
}//结果会打印出0,1,2,3,4,5
{{< / highlight >}}
因为每次循环都会多创建一个i，就生成了6个不同的值。

---
{{< highlight js>}}
let i = 0
let fn = (a) => {
  setTimeout(() => {
    console.log(a)
  }, 0)
}
for (i = 0; i < 6; i++) {
  fn(i)
}
{{< / highlight >}}
这样也能打印出0,1,2,3,4,5。个人认为可能和上一段代码一样，每次循环都会生成一个a，这样就生成了6个不同的a值。