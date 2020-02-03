---
title: "《HTML入门笔记1》"
date: 2020-02-01T19:46:43+08:00
draft: false
---

# 前端学习

## 《HTML 入门笔记 1》

### 一、HTML 的发明者

蒂姆·伯纳斯·李（Tim Berners-Lee）

- 2004 年，英女皇伊丽莎白二世向 Tim Berners-Lee 颁发大英帝国爵级司令勋章。
- 2012 年夏季奥林匹克运动会开幕典礼上，他获得了“万维网发明者”的美誉。
- 2017 年，他因“发明万维网、第一个浏览器和使万维网得以扩展的基本协议和算法”而获得 2016 年度的图灵奖。

### 二、HTML 起手式

HTML 起手式如下：

```
<!DOCTYPE html>
 <html lang="en">
   <head>
     <meta charset="UTF-8" />
     <meta name="viewport" content="width=device-width, initial-scale=1.0" />
     <meta http-equiv="X-UA-Compatible" content="ie=edge" />
     <title>Document</title>
   </head>
   <body>

   </body>
 </html>
```

内容解析：

1. `<!DOCTYPE html>`表示文档类型,告诉浏览器用 HTML 解析网页；
2. `<html lang="en">`表示此页面的语言为英文，可将 en 改为 zh-CN，从而将页面语言改为中文简体；
3. HTML 两个子元素之一：head，它的内容不会出现在网页上，而是为网页渲染做准备；

- `<meta charset="UTF-8" />`表示此文件的字符编码为 UTF-8,建议统一采用 UTF-8；
- `<meta name="viewport" content="width=device-width, initial-scale=1.0" />`表示防止页面缩放；
- `<meta http-equiv="X-UA-Compatible" content="ie=edge" />`如果当前页面在 IE 浏览器显示，告诉 IE 使用最新内核；
- `<title>Document</title>`表示此网页的标题为 Document。

4. HTML 两个子元素之二：body。

### 三、章节标签

表示文章/书的层级。

1. 标题 h1~h6

HTML 提供了 6 个标签，用于表示文章的标题。按照标题的等级，分为如下六级标题：

- h1：一级标题；
- h2：二级标题；
- h3：三级标题；
- h4：四级标题；
- h5：五级标题；
- h6：六级标题。

```
<h1>文章标题</h1>
 <h2>第一章</h2>
 <h3>1.1节</h3>
```

2. 章节 section

`section`标签表示一个含有主题的独立部分，通常用在文档里面表示一个章节。`section`总是多个一起使用，一个页面不能只有一个`section`。

```
<h1>文章标题</h1>
 <section>
   <h2>第一章</h2>
   <p>段落内容</p>
 </section>
```

3. 文章 article

`article`标签表示页面里面一段完整的内容，即使页面的其他部分不存在，也具有独立使用的意义，通常用来表示一篇文章或者一个论坛帖子。

```
<article>
   <h2>文章标题</h2>
   <p>文章内容</p>
 </article>
```

4. 段落 p

`p`标签表示文章的一个段落(paragraph)。

`<p>段落内容</p>`

5. 头部 header

`header`标签既可以表示整个网页的头部，也可以表示一篇文章或者一个区块的头部。

`<header>顶部广告</header>`可用于显示顶部广告。

6. 脚部 footer

`footer`标签表示网页、文章或章节的尾部，通常包含版权信息或者其他相关信息。

`<footer>&copy;XX版权所有。</footer>`显示为 © XX 版权所有。

7. 主要内容 main

`main`标签表示页面的主体内容，一个页面只能有一个。

```
<body>
   <header>页眉</header>
   <main>
     <article>文章</article>
   </main>
   <footer>页尾</footer>
 </body>
```

8. 旁支内容 aside

`aside`标签用来放置与网页或文章主要内容间接相关的部分,可以用来放置网页侧边栏、文章评论或注释等。

```
<body>
   <main>主体内容</main>
   <aside>侧边栏</aside>
 </body>
```

9. 划分 div

`div`是一个通用标签，表示一个区块（division）。

```
<body>
   <header>页眉</header>
   <div>
     <main>
       <article>文章</article>
     </main>
     <aside>注释</aside>
   </div>
   <footer>页尾</footer>
 </body>
```

### 四、全局属性

全局属性为所有标签都有的属性。

1. class

`class`属性用于对网页元素进行分类。

`<div class="middle">`为标签添加 class 属性，可进行 style 设置。

2. contenteditable

HTML 网页的内容默认是用户不能编辑，`contenteditable`属性允许用户修改内容。

`<div contenteditable>`可使区域内元素被编辑。

3. hidden

`hidden`属性表示当前的网页元素不再跟页面相关，不会在网页中看到它。

`<p hidden>本句不会出现在网页中。</p>`此代码中的 p 元素不会出现在网页中。

4. id

`id`属性用于表示全局唯一的标签，不是唯一的用 class。但是 id 的全局唯一性没有保障，就算有两个重复的 id，HTML 也不会提示错误，因此不到万不得已不要使用 id。

```
<div id="xxx">
   <main>
     <article>文章</article>
   </main>
     <aside>注释</aside>
 </div>
```

5. style

`style`属性用于指定当前元素的 CSS 样式。

- `style`一般放在 head 中。

```
<style>
   [class="middle"] {
     background: black;
     color: white;
   }
 </style>
```

- 将`style`放在 body 中时：

  ① 加一句 `style{display: block;}`可使 style 在页面上显示；

  ② 将 style 属性设置为 contenteditable 时，可实现在页面显示的 style 中对其进行编辑，改变 style 样式。

```
<style contenteditable>
   style {
     display: block;
     border: 5px solid yellow;
   }
   [class="middle"] {
     background: black;
     color: white;
   }
 </style>
```

6. tabindex

`tabindex`属性的值是一个整数，表示用户按下 Tab 键的时候，网页焦点转移的顺序。不同的属性值有不同的含义。

- `tabindex="-1"`表示不参与 Tab 键对网页元素的遍历；
- `tabindex="0"`表示该元素参与 Tab 键的遍历，且顺序为最后；
- `tabindex="正整数"`网页元素按照从小到大的顺序（1、2、3、……），参与 Tab 键的遍历。如果多个元素的 tabindex 属性相同，则按照在网页源码里面出现的顺序遍历。

7. title

`title`属性用来为元素添加附加说明。大多数浏览器中，鼠标悬浮在元素上面时，会将`title`属性值作为浮动提示显示出来。

- 在 head 的 style 中添加以下 style

```
<style>
   [class="top"] {
     white-space: nowrap; <!--不要换行-->
     overflow: hidden; <!--溢出就省略-->
     text-overflow: ellipsis; <!--省略的部分用省略号表示-->
   }
 </style>
```

- 在 body 中输入如下内容：

```
<header class="top" title="顶部广告的完整内容">顶部广告</header>
```

通过上面两个操作可实现只显示一行广告，鼠标悬浮在广告上面时显示完整内容的效果。

### 五、内容标签

1. ol+li (ordered list + list item)

`ol`标签是一个有序列表容器（ordered list），会在内部的列表项前面产生数字编号。列表项的顺序有意义时，比如排名，就会采用这个标签。

`li`标签表示列表项，用在`ol`或`ul`之中。

```
<ol>
   <li>列表项 A</li>
   <li>列表项 B</li>
   <li>列表项 C</li>
 </ol>
```

2. ul+li (unordered list + list item)

`ul`标签是一个无序列表容器（unordered list），会在内部的列表项前面产生实心小圆点，作为列表符号。列表项的顺序无意义时，采用这个标签。

```
<ul>
   <li>列表项 A</li>
   <li>列表项 B</li>
   <li>列表项 C</li>
 </ul>
```

3. dl+dt+dd

`dl`标签是一个块级元素，表示一组术语的列表（description list）。术语名（description term）由`dt`标签定义，术语解释（description detail）由`dd`标签定义。

```
<dl>
   <dt>HTML</dt>
   <dd>超文本标记语言</dd>
 </dl>
```

4. pre (preview 的缩写)

`per`标签表示保留原来的格式，可用于使浏览器保留该标签内部原始的换行和空格等特殊符号。浏览器默认以等宽字体显示标签内容。

```
<pre>left    right</pre>
```

5. hr

`hr`标签用于分隔两个不同的主题，浏览器会将其渲染为一根水平线。该标签是单独使用的，没有闭合标签。

```
<p>第一个主题</p>
 <hr>
 <p>第二个主题</p>
```

6. br (break 的缩写)

`br`标签让网页产生一个换行效果。该标签是单独使用的，没有闭合标签。

```
<p>
   昨夜雨疏风骤, <br>
   浓睡不消残酒。<br>
   试问卷帘人,<br>
   却道海棠依旧。<br>
   知否,知否, <br>
   知否应是绿肥红瘦。
 </p>
```

7. a (anchor 的缩写)

`a`标签可用于定义超链接，用户点击后浏览器会跳转到指定的网址。

```
<a href="https://wikipedia.org/">维基百科</a>
```

8. em (emphasis 的缩写)

`em`标签表示强调（emphasis），语气上的强调，浏览器默认会以斜体显示它包含的内容。

```
<p>我们<em>本次期末考试</em>的重点是JavaScript</p>
```

9.  strong

`strong`标签表示它包含的内容本身具有很强的重要性，需要引起注意。浏览器会以粗体显示内容。

```
<p>我们本次期末考试的重点是<strong>JavaScript</strong></p>
```

10. code

`code`标签表示标签内容是计算机代码，浏览器默认会以等宽字体显示。

```
<pre>
 <code>
 var a=1;
 console.log(a);
 </code>
 </pre>
```

11. q (quote 的缩写)

`q`标签表示引用。

```
<p>
   莎士比亚的《哈姆雷特》有一句著名的台词：<q>活着还是死亡,这是一个问题。</q>
 </p>
```

上面代码显示结果为：
莎士比亚的《哈姆雷特》有一句著名的台词："活着还是死亡，这是一个问题。"

12. blockquote

`blockquote`标签表示引用，它与`q`标签的区别，就是会产生换行。

```
<p>
   莎士比亚的《哈姆雷特》有一句著名的台词：<blockquote>活着还是死亡,这是一个问题。</blockquote>
 </p>
```

上面代码显示结果为：

莎士比亚的《哈姆雷特》有一句著名的台词：

活着还是死亡,这是一个问题。
