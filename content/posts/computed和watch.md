---
title: "Computed和watch"
date: 2020-01-11T12:53:50+08:00
draft: true
---

```javascript
let selectSort = (arr) => {
  if (arr.length === 0) {
    console.log("输入的为空数组！")
  } else {
    for (let i = 0; i < arr.length - 1; i++) {
      let j = minIndex(arr.slice(i)) + i
      if (j !== i) {
        swap(arr, i, j)
      }
    }
  }
  return arr
}
```