---
title: "《CSS  知识总结》"
date: 2020-02-24T23:49:33+08:00
draft: false
---

# 前端学习

## 《CSS 知识总结》

### 一、CSS 基础知识

#### 1. 文档流（Normal Flow）

- `inline`

流动方向：元素从左到右，到达最右边才会换行，遇到行尾折行；

宽度：为内部 inline 元素的和，不能用 width 指定；

高度：由 line-height 间接确定，跟 height 无关；没有内容的 inline 元素高度为 line-height，不为 0。

- `block`

流动方向：元素从上到下，每一个都另起一行；

宽度：默认自动计算宽度，可用 width 指定；

高度：由内部文档流元素决定，可以设 height，没有内容的 block 元素高度为 0。

- `inline-block`

流动方向：从左到右，但是像 block 元素一样不会跨行。

宽度：为内部元素的和，可用 width 指定。

高度：由内部文档流元素决定，可以设 height；

- 脱离文档流的方式：① float；② position 为 absolute 或者 fixed。

#### 2. CSS 盒模型

CSS 盒模型有两种：`content-box` 和 `border-box`，默认为 `content-box`，但一般优先使用 `border-box`。

`content-box` 的宽度 width 表示内容区的宽度，不包含 `padding` 和 `border`；

`border-box` 的宽度 width 表示内容区 + `padding` + `border` 的总和。

#### 3. 常用代码

- `list-style:none;`

去掉 `ol` 或者 `ul` 中的 `li` 前面的数字或者圆点。

- `vertical-align:middle;`

去掉图片下面的多余背景色，取值为 top 或者 bottom 也可实现该功能。

- `outline:1px solid red;`

代替 border，取消 border 对 width 的干扰。

- `margin:0 auto;`

可实现居中，但是会覆盖上下的 margin。

- `margin-left:auto;margin-right:auto;`

可实现块元素居中，且不会覆盖上下的 margin。

- `transform:translate(-50%,-50%);`

可做绝对定位元素的居中。

### 二、CSS 布局

#### 1. 选择布局方式

Float 布局：需要兼容 IE9；

Flex 布局：不需要兼容 IE9，需兼容老版浏览器；

Grid 布局：不需要兼容 IE9，且只兼容最新浏览器。

#### 2. Float 布局

- 在子元素上加 float:left 和 width；

* 在父元素上加.clearfix。

```
.clearfix:after{
  content:'';
  display:block;
  clear:both;
}
```

#### 3. Flex 布局

Flex 布局包括容器（container）和项目（items）。

- flex container 属性

① `display:flex;`

让一个元素变成 flex 容器。

```
.container {
  display: flex;
}
```

② 改变 items 流动方向

```
.container {
  flex-direction: row/row-reverse/column/colum-reverse;
}
```

`row`: 元素摆放的方向和文字方向一致。

`row-reverse`: 元素摆放的方向和文字方向相反。

`column`: 元素从上放到下。

`column-reverse`: 元素从下放到上。

③ 改变折行

```
.container {
  flex-wrap: nowrap/wrap/wrap-reverse;
}
```

`nowrap`: 所有的元素都在一行。

`wrap`: 元素自动换成多行。

`wrap-reverse`: 元素自动换成逆序的多行。

注意：`flex-direction` 和 `flex-wrap` 可以进行缩写，例如：`flex-flow：column wrap;`

④ 主轴对齐方式

```
.container {
  justify-content: flex-start/flex-end/center/space-between/space-around/space-evenly;
}
```

`flex-start`: 元素和容器的左端对齐。

`flex-end`: 元素和容器的右端对齐。

`center`: 元素在容器里居中。

`space-between`:元素之间保持相等的距离。

`space-around`:元素周围保持相等的距离。

当要使两个子元素左右对齐时，可使用 `justify-content:space-between;` 或者在后一个子元素上加 `margin-left:auto;` 。

⑤ 次轴对齐

```
.container {
  align-items: stretch/flex-start/flex-end/center;
}
```

`stretch`: 元素被拉伸以填满整个容器。

`flex-start`: 元素与容器的顶部对齐。

`flex-end`: 元素与容器的底部对齐。

`center`: 元素纵向居中。

⑥ 多行内容

```
.container {
  align-content: flex-start/flex-end/center/stretch/space-between/space-around;
}
```

`flex-start`: 多行都集中在顶部。

`flex-end`: 多行都集中在底部。

`center`: 多行居中。

`stretch`: 每一行都被拉伸以填满容器。

`space-between`: 行与行之间保持相等距离。

`space-around`: 每行的周围保持相等距离。

- flex item 属性

① `order`

`order`元素的属性默认值为 0，设置 `order` 可改变 `item` 的顺序，数字越小越靠前，负数在 0 之前。

② `flex-grow`

控制如何增大，数字越大增的越快。

③ `flex-shrink`

控制如何缩小，数字越大缩的越快。`flex-shrink:0;` 防止变瘦。

④ `align-self`

可定制 `align-items` ，这个属性接受和 `align-items` 一样的值。

#### 4. Grid 布局

Grid 布局包括容器（container）和项目（items）。

- grid container 属性

① `display:grid;`

让一个元素变成 grid 容器。

```
.container {
  display: grid;
}
```

② 行和列

```
.container {
  grid-template-rows: 25% 100px auto;
  grid-template-columns: 40px 50px auto 50px 40px;
}
```

上面代码定义了一个 3 行 5 列的布局。

③ `grid-column-start` 和 `grid-column-end`

若仅使用 `grid-column-start`，网格默认只占一列。同时使用 `grid-column-start`和 `grid-column-end` 可将网格拓展到多列。

`grid-column-start`和 `grid-column-end`的缩写为：`grid-column:开始行/结束行;`。

`grid-row-start` 就像 `grid-column-start` 一样，只不过是在垂直方向指定起始位置。

```
.container {
  grid-column-start: 2;
  grid-column-end: span 2;
}
.container {
  grid-column-start: 2;
  grid-column-end: 4;
}
```

可以用`span`来指定所要跨越的宽度，以上两组代码实现功能一样。

`grid-column` 和 `grid-row` 的缩写是 `grid-area`，`grid-area:开始行/开始列/结束行/结束列;`。

- flex item 属性

`order`元素的属性默认值为 0，设置 `order` 可改变 `item` 的顺序，数字越小越靠前，负数在 0 之前。

### 三、CSS 定位

#### 1. position 属性

- `position:static`：默认值，元素出现在正常的文档流中。

- `position:relative`：相对定位，不脱离文档流也不影响其他元素，元素是在文档中的正常位置偏移给定的值。

- `position:absolute`：绝对定位，元素脱离了文档流，并不为元素预留空间。通过指定元素相对于最近的非 static 定位祖先元素的偏移，来确定元素位置。绝对定位的元素可以设置外边距（margins），且不会与其他边距合并。

- `position:fixed`：固定定位，元素脱离了文档流，并不为元素预留空间。通过指定元素相对于屏幕视口（viewport）的位置来指定元素位置。但是会被某些属性影响，例如：`transform:scale(0.9);`。

- `position:sticky`：粘滞定位,可以被认为是相对定位和固定定位的混合。元素在跨越特定阈值前为相对定位，之后为固定定位。偏移值不会影响任何其他元素的位置。

强调：

① 如果写了 absolute，一般都得补一个 relative；

② 如果写了 absolute 或者 fixed，一定要补 top/bottom 和 left/right；

③ sticky 兼容性很差，通常得加一句 position:-webkit-sticky。

#### 2. 创建层叠上下文

- 根元素（HTML）；

- `position:fixed;`；

- `z-index` 值不为“auto”的绝对/相对定位；

- 一个 `z-index` 值不为“auto”的 flex 项目（flex item），即：父元素 `display:flex/inline-flex;`；

- `opacity` 属性值小于 1 时，例如：`opacity:0.5;`；

- `transform` 属性值不为“none”的元素。

### 四、浏览器渲染原理

#### 1. 渲染步骤

- 根据 HTML 构建 HTML 树（DOM);

- 根据 CSS 构建 CSS 树（CSSOM）；

- 将两棵树合并成一颗渲染树（render tree）；

- Layout 布局，包括文档流、盒模型、计算大小和位置；

- Paint 绘制，把边框颜色、文字颜色、阴影等画出来；

- Compose 合成，根据层叠关系展示画面。

#### 2. 渲染方式

- JS/CSS>样式>布局>绘制>合成

- JS/CSS>样式>绘制>合成

- JS/CSS>样式>合成

[查看元素属性触发什么流程](https://csstriggers.com/)

### 五、CSS 动画

#### 1. transform

`transform` 属性可对给定元素实现平移，缩放，旋转或倾斜转换。但是只能转换由盒模型定位的元素。

- `transform:none`： 默认值，不做任何变换。

- `transform:translate`：位移，translateX 横向移动，translateY 纵向移动，translateZ 垂直于平面运。translateX 和 translateY 可缩写为 translate；translateX 、translateY 和 translateZ 可缩写为 translate3d。

- `transform:scale`：缩放，scaleX 横向缩放,scaleY 纵向缩放，缩写为 scale，因为容易出现模糊而用的比较少。

- `transform:rotate`：默认为沿 Z 轴旋转，一般用于 360 度旋转制作 loading，表示加载中。

- `transform:skew`：skewX 为 X 方向倾斜度数，skewY 为 Y 方向倾斜度数，它们的缩写为 skew。

#### 2. transition

`transition` 可用于补充转换前和转换后的中间帧，从而实现动画效果。

- `transition`语法：transition：属性名 时长 过渡方式 延迟

* 可以用逗号分隔两个不同属性，例如：`transition:left 200ms,top 400ms;`；

* 可以用 all 代表所有属性；

* 过渡方式：linear/ease/ease-in/ease-out/ease-in-out/cubic-bezier/step-start/step-end/steps；

#### 3. animation

`animation` 属性是 `animation-name`，`animation-duration`, `animation-timing-function`，`animation-delay`，`animation-iteration-count`，`animation-direction`，`animation-fill-mode` 和 `animation-play-state` 属性的一个简写属性形式。

- `animation` 语法：animation:时长/过渡方式/延迟/次数/方向/填充模式/是否暂停/动画名;

* 时长：1s 或者 1000ms

* 过渡方式：跟 `transition` 取值一样

* 次数：定义动画几次，infinite 表示无限次

* 方向：reverse（反向）/alternate（交替的，先去后回）/alternate-reverse（交替的，先回后去）

* 填充模式：none/forwards（向前的，指不要再回来）/backwards/both

* 是否暂停：paused/running
