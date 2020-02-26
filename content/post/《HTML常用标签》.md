---
title: "《HTML常用标签》"
date: 2020-02-15T01:00:51+08:00
draft: false
---

# 前端学习

## 《HTML 常用标签》

### 一、a 标签的用法

HTML 的 `a`标签可以创建通向其他网页、文件、电子邮件地址、电话、同一页面内的位置或任何其他 URL 的超链接。

`a`标签有如下属性：

#### 1. href

`href` 属性给出超链接指向的网址。它的值应该是一个 URL 或者锚点。

- 网址

链接通过`a`标签表示，用户点击后，浏览器会跳转到指定的网址。

```
<a href="https://google.com">Google</a>
 <a href="http://google.com">Google</a>
 <a href="//google.com">Google</a>
```

上面三条代码都定义了一个超链接，浏览器将显示三个“Google”，文字下面默认会有下划线，表示这是一个链接。用户点击任一“Google”后，浏览器都将跳转到 Google 首页。推荐使用`//google.com`，因为`//`最高级，它会自动选择适用 https 还是 http。

`a`标签内部不仅可以放置文字，也可以放置其他元素，比如段落、图像、多媒体等等。

```
<a href="https://google.com"><img src="google.png"/></a>
```

上面代码中，`a`标签内部就是一个图像。用户点击图像，就会跳转到指定网址。

- 路径

链接也可以指向一个文件，用户点击后，浏览器打开文件内容。

① 链接到当前文件中的 a/b/c.html 的两种方式

```
<a href="/a/b/c.html">c.html</a>
 <a href="a/b/c.html">c.html</a>
```

② 链接到当前目录中的 index.html 的两种方式

```
<a href="index.html">index.html</a>
 <a href="./index.html">index.html</a>
```

- 伪协议

① javascript:代码；

链接也可以指向一个 javascript 代码，用户点击后，浏览器执行代码。

```
<a href="javascript:alert(1);">javascript 伪协议 1</a>
```

上面代码中，链接就指向 javascript 代码。点击后，浏览器会执行代码，显示结果为“1”。

空的 javascript 代码也是允许的，就像下面这样。点击后，访问 a 标签，但是页面什么都不做。

```
<a href="javascript:;">空的伪协议</a>
```

② mailto:邮箱

链接也可以指向一个邮件地址，使用`mailto`协议。用户点击后，浏览器会打开本机默认的邮件程序，让用户向指定的地址发送邮件。

```
<a href="mailto:143****038@qq.com">发邮件给XX</a>
```

上面代码中，链接就指向邮件地址。点击后，浏览器会打开一个邮件地址，让你可以向 143\*\*\*\*038@qq.com 发送邮件。

不指定邮箱也是允许的，就像下面这样。这时用户自己在邮件程序里面，填写想要发送的邮箱，通常用于邮件分享网页。

```
<a href="mailto:">发邮件</a>
```

③ tel:手机号

如果是手机浏览的页面，还可以使用`tel`协议，创建电话链接。用户点击该链接，会唤起电话，可以进行拨号。

```
<a href="tel:158****2456">打电话给158****2456</a>
```

- id

跳转到内部锚点。

```
<a href="#xxx">查看xxx</a>
```

上面代码中，`href`属性的值是#加上锚点名称。点击后，浏览器会自动滚动，停在当前页面里面 xxx 锚点所在的位置。

#### 2. target

`target`属性指定如何展示打开的链接。它可以是在指定的窗口打开，也可以在`iframe`里面打开。

- `_self`:在当前窗口打开，如果没有指定属性`_self`为默认值。

```
<a href="//baidu.com" target="_self">self</a>
```

- `_blank`:在新窗口打开。

```
<a href="//baidu.com" target="_block">blank</a>
```

- `_parent`：在上层窗口打开，这通常用于从父窗口打开的子窗口，或者`iframe`里面的链接。如果当前窗口没有上层窗口，这个值等同于`_self`。

```
<a href="//baidu.com" target="_parent">parent</a>
```

- `_top`：在顶层窗口打开。如果当前窗口就是顶层窗口，这个值等同于`_self`。

```
<a href="//baidu.com" target="_top">top</a>
```

`target`还能实现在指定的窗口打开。下面代码中，两个链接都在名叫 test 的窗口打开。首先点击链接 Google，浏览器发现没有叫做 test 的窗口，就新建一个窗口，起名为 test，在该窗口打开 google.com。然后，用户又点击链接 baidu，由于已经存在 test 窗口，浏览器就在该窗口打开 baidu.com，取代里面已经打开的 google.com。

```
<a href="//google.com" target="test">Google</a>
 <a href="//baidu.com" target="test">baidu</a>
```

### 二、img 标签的用法

`img`标签用于发出 get 请求，展示一张图片。它是单独使用的，没有闭合标签。

`img`标签有如下属性：

#### 1. src

`src`属性指定图片的网址，下例是相对 URL，表示图片与网页在同一个目录。

```
<img src="蛋糕.png"/>
```

#### 2. alt

alt 属性用来设定图片的文字说明。图片不显示时（比如下载失败，或用户关闭图片加载），图片的位置上会显示该文本。

```
<img src="蛋糕.png" alt="蛋糕" />
```

上面代码中，alt 是图片的说明。图片下载失败时，浏览器会在图片位置，显示文字“蛋糕”。

#### 3. width/height

图片默认以原始大小插入网页，`width`属性和`height`属性可以指定图片显示时的宽度和高度，单位是像素或百分比。

```
<img src="蛋糕.png" width="200" height="150" />
```

上面代码中，`width`属性指定图片显示的宽度为 200 像素，`height`属性指定显示高度为 150 像素。

如果`width`和`height`同时设置，可能造成图片变形，通常`width`和`height`只设置其中一个，这时浏览器会根据图片的原始大小，自动设置对应比例的图片宽度或高度。

### 三、table 标签的用法

`table`是一个块级容器标签，所有表格内容都要放在这个标签里面。

`table`有如下子元素：

#### 1. caption

`caption`总是`table`里面的第一个子元素，表示表格的标题。该元素是可选的。

```
<caption>二年级一班成绩表</caption>
```

#### 2. thead、tbody、tfoot

`thead`、`tbody`、`tfoot`都是块级容器元素，且都是`table`的一级子元素，分别表示表头、表体和表尾。这三个元素都是可选的，在源代码中没有先后顺序要求。

```
<table>
   <thead>... ...</thead>
   <tbody>... ...</tbody>
   <tfoot>... ...</tfoot>
 </table>
```

#### 3. tr

`tr`标签表示表格的一行（table row）。如果表格有`thead`、`tbody`、`tfoot`，那么`tr`就放在这些容器元素之中，否则直接放在`table`的下一级。

```
<table>
   <tr>...</tr>
   <tr>...</tr>
 </table>
```

上面代码表示表格共有 2 行。

#### 4. th、td

`th`和`td`都用来定义表格的单元格。其中，`th`是标题单元格，`td`是数据单元格。

```
<table>
       <thead>
         <tr><th></th><th>张小红</th><th>小明</th><th>小颖</th></tr>
       </thead>
       <tbody>
         <tr><th>数学</th><td>61</td><td>91</td><td>85</td></tr>
         <tr><th>语文</th><td>79</td><td>82</td><td>92</td></tr>
         <tr><th>英语</th><td>100</td><td>97</td><td>87</td></tr>
       </tbody>
       <tfoot>
         <tr><th>总分</th><td>240</td><td>270</td><td>264</td></tr>
       </tfoot>
     </table>
```

上面代码中，表格为一个成绩单，第一行是标题行，所以使用`th`；第二行和第五行中的分数是数据，所以使用`td`。

#### `table`标签的相关样式

- `table-layout`：是 CSS 属性，定义用于布局表格单元格、行和列的算法。

`table-layout`取值为`auto`时，表示采用自动表格布局算法对表格布局，表格及单元格的宽度取决于其包含的内容。

```
table {
 table-layout: auto;
 }
```

`table-layout`取值为`fixed`时，表格和列的宽度通过表格的宽度来设置，某一列的宽度仅由该列首行的单元格决定。在当前列中，该单元格所在行之后的行并不会影响整个列宽。通常可结合`width`属性来限制表格的宽。

```
table {
  table-layout: fixed;
  width: 120px;
 }
```

- `border-collapse`： 是 CSS 属性，用来决定表格的边框是分开的还是合并的。在分隔模式下，相邻的单元格都拥有独立的边框。在合并模式下，相邻单元格共享边框。

`border-collapse`取值为`collapse`时，相邻的单元格共用同一条边框。

```
table {
 border-collapse: collapse;
 }
```

`border-collapse`取值为`separate`时，每个单元格拥有独立的边框，它是默认值。

```
table {
 border-collapse: separate;
 }
```

- `border-spacing`:指定相邻单元格边框之间的距离，该属性只适用于`border-collapse`值是`separate`的时候。

```
table {
 border-spacing: 2px;
 }
```

上面代码表示单元格边框之间的距离为 2 像素。

### 四、表单标签的用法

#### 1. form 标签的用法

`form`标签用来定义一个表单，所有表单内容放到这个容器元素之中。

`form`有如下属性：

- `action`：服务器接收数据的 URL。

* `method`：提交数据的 HTTP 方法，可能的值有`POST`（表单数据作为 HTTP 数据体发送），`GET`（表单数据作为 URL 的查询字符串发送）。

* `autocomplete`：如果用户没有填写某个控件，浏览器是否可以自动填写该值。它的可能取值分别为`off`（不自动填写）和`on`（自动填写）。

* `target`：在哪个窗口展示服务器返回的数据。

```
<form action="https://example.com/api" method="post" autocomplete="on" target="_blank">
   <input type="text" name="user">
   <input type="submit">
 </form>
```

上面代码就是一个表单，包含一个文本输入框和一个提交按钮，文本输入框的`name`属性是`user`。用户在文本输入框里面，输入用户名，比如 Lucy，然后点击提交按钮，浏览器就会向服务器https://example.com/api发送一个 POST 请求，发送 user=Lucy 这样一段数据，并在一个空白窗口展示服务器返回的数据。

#### 2. input 标签的用法

`input`标签是一个行内元素，用来接收用户的输入。它是一个单独使用的标签，没有结束标志。

`input`有多种类型，取决于`type`属性的值。`type`属性有如下取值：

- `type="text"`：普通的文本输入框，用来输入单行文本。

```
<input name="username" type="text" />
```

- `type="email"`：一个只能输入电子邮箱的文本输入框。表单提交之前，浏览器会自动验证是否符合电子邮箱的格式，如果不符合就会显示提示，无法提交到服务器。

```
<input name="email" type="email" />
```

- `type="password"`：一个密码输入框。用户的输入会被遮挡，字符通常显示星号“\*”或点“·”。

```
<input name="password" type="password" />
```

- `type="radio"`：单选框，表示一组选择之中，只能选中一项。单选框通常为一个小圆圈，选中时会被填充或突出显示。

```
<input name="gender" type="radio" />男
 <input name="gender" type="radio" />女
```

- `type="checkbox"`：复选框，允许选择或取消选择该选项。

```
<input name="hobby" type="checkbox" />网球
 <input name="hobby" type="checkbox" />篮球
 <input name="hobby" type="checkbox" />乒乓球
 <input name="hobby" type="checkbox" />游泳
```

- `type="file"`：一个文件选择框，常用于文件上传功能。默认只能选择一个文件，添加`multiple`属性后允许选择多个文件。

```
<input name="file" type="file" />
 <input name="files" type="file" multiple />
```

- `type="submit"`：表单的提交按钮。用户点击这个按钮，就会把表单提交给服务器。如果不指定`value`属性，浏览器会在提交按钮上显示默认的文字，通常是“提交”。

```
<input type="submit" value="保存并提交" />
```

注意：`form`里面放一个`type="submit"`才能触发 submit 事件。

#### 更多`type`属性请前往[HTML 教程](https://wangdoc.com/html/form.html)学习。
