---
title: "HTML常用标签"
date: 2019-10-04T11:22:38+08:00
draft: true
---

# HTML 常用标签

## 1.a 标签的用法

### 属性

1. **href** （超链接）

   ##### 1.1 href 的取值

   - 网址  
     https://google.com
     http://google.com
     //google.com（推荐）
   - 路径  
     /a/b/c 以及 a/b/c
   - 伪协议  
     javascript:代码  
     mailto:邮箱  
     tel:手机号
   - ID 跳转到指定标签  
     href=#xxxx
   - 代码示例:

     ```
     <body>
     <p>1</p>
     <p>2</p>
     <p id="xxx">3</p>
     <p>4</p>
     <a href="https://baidu.com" target="_blank">超链接</a>
     <a href="/a/b/c.html">c.html</a>
     <a href="index.html">index</a>
     <a href="javascript:alert(1);">JavaScript伪协议</a>
     <a href="javascript:;">空的伪协议</a>
     <a href="#xxx">查看xxx</a>
     <a href="mailto:xxxxxxxx@qq.com">发邮件</a>
     <a href="tel:10010">打电话</a>
     </body>
     ```

   ##### 1.2 a 的 target 的取值

   - 内置名字  
     \_blank（新页面）
     \_top（最顶层页面）
     \_parent（当前所在页面的上一层）
     \_self（当前页面）

   - 程序员命名
     window 的 name（="xxx"，会覆盖之前的页面）
     iframe 的 name

   - 代码示例:

     ```
     <a href="https://baidu.com" target="_blank">百度</a>
     <a href="https://baidu.com" target="_top">百度</a>
     <a href="https://baidu.com" target="_parent">百度</a>
     <a href="https://baidu.com" target="_self">百度</a>
     <a href="https://baidu.com" target="xxx">百度</a>
     <iframe src="" name="xxx"></iframe>
     ```

2. **target**（指定在哪里打开超链接）
3. **download**（下载网页）
4. **rel=noopener**（防 bug）

### 作用

1. 跳转外部页面
2. 跳转内部锚点
3. 跳转到邮箱或电话等

## 2.img 标签的用法

### 作用

发出 get 请求，展示一张图片

### 属性

alt/height/width/scr

### 事件

onload/onerror（图片是否加载成功）

代码示例：

```
<img id="xxx" width="400" src="C&T.png" alt="一张图片" />
    <script>
      xxx.onload = function() {
        console.log("加载成功");
      };
      xxx.onerror = function() {
        console.log("加载失败");
        xxx.src = "/截图4.png";
      };
    </script>
```

### 响应式

max-width:100%

代码示例：

```
<style>
      * {
        margin: 0;
        padding: 0;
        box-sizing: border-box;
      }
      img {
        max-width: 100%;
      }
    </style>

```

## 3.table 标签的用法

### 相关的标签

- table
- thead
- tbody
- tfoot
- tr(table 中的一行)
- td(数据)
- th(表头)
- 代码示例:

  ```
  <table>
      <thead>
        <tr>
          <th>英语</th>
          <th>翻译</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <td>hyper</td>
          <td>超级</td>
        </tr>
        <tr>
          <td>target</td>
          <td>目标</td>
        </tr>
        <tr>
          <td>error</td>
          <td>错误</td>
        </tr>
      </tbody>
      <tfoot>
        <tr>
          <td>空</td>
          <td>空</td>
        </tr>
      </tfoot>
    </table>
  ```

  ![捕获1.PNG](https://i.loli.net/2019/10/04/uGtL3b7lNY4xQMr.png)

### 相关的样式

- table-layout,定义了用于布局表格单元格，行和列的算法。

  ![捕获2.PNG](https://i.loli.net/2019/10/04/fHg6DeZzVPdLcbU.png)

- border-collapse,是用来决定表格的边框是分开的还是合并的。在分隔模式下，相邻的单元格都拥有独立的边框。在合并模式下，相邻单元格共享边框。
- border-spacing,指定相邻单元格边框之间的距离（只适用于边框分离模式 ）。
- 代码示例:
  ```
  <style>
      table {
        width: 600px;
        table-layout: auto;
        border-spacing: 0;
        border-collapse: collapse;
      }
      td,
      th {
        border: 1px solid blue;
      }
    </style>
  ```
  ![捕获3.PNG](https://i.loli.net/2019/10/04/dAyQ4KJEuYTW1Pj.png)

## 4.感想总结

1. 不要双击打开 HTML，运行`http-server . -c-1`(简写`hs -c-1`)，加上/a-href.html 或者运行 `parcel a-href.html`
2. 不要让图片变形
3. form 标签，作用：发 get 或 post 请求，然后刷新页面

   - action(后端给的)
   - autocomplete(自动提示)
   - method(改 get 或 post)
   - target(哪个页面要刷新)

4. button 里面可以有标签，input 不行
5. input 标签，作用：让用户输入内容
6. 隐藏的 input 是 JS 自动填写用的
7. 一般不监听 input 的 click 事件
8. form 里面的 input 要有 name
9. form 里面要放一个 type=submit 才能触发 submit 事件  
   代码示例：

```
<body>
    <form action="/xxx" method="POST" autocomplete="on" target="_blank">
      <input name="username" type="text" required />
      <input type="color" />
      <hr />
      <input type="password" />
      <hr />
      <input name="gender" type="radio" />男
      <input name="gender" type="radio" />女
      <hr />
      <input type="checkbox" />
      <hr />
      <input type="file" />
      <input type="file" multiple />
      <hr />
      <textarea style="resize: none;"></textarea>
      <hr />
      <select>
        <option value="1">周一</option>
        <option value="2">周二</option>
      </select>
      <input type="submit" value="搞起" />
      <button type="submit"><strong>搞起</strong></button>
    </form>
  </body>
```
