# Flexbox 笔记整理

## 简介

翻译 W3C 对 Flex 布局的简介如下：

> 在 flexbox 的布局模型中，一个 flexbox 容器的子元素可以被放置在任何方向上，并且它们的尺寸可以被弹性调节，从而填充未被使用的空间或者缩小来避免超出父级元素。在 flexbox 布局中，子元素的水平和垂直的对齐的操纵变得十分方便。这些嵌套可以用于网页上二维的布局。

## 兼容性

Flexbox 目前仍然不是正式标准，因此兼容性上还有一些限制。目前 Flexbox 兼容的浏览器如下：

 - Internet Explorer 11 / Edge 可以提供完整的支持，10 提供部分支持，需要加上前缀 -ms-
 - Chrome 31 以上版本
 - Firefox 31 以上版本
 - Safari 7 以上版本
 - Opera 29 以上版本
 - Android 4.4 以上的自带浏览器可以提供完整的支持，4.1-4.3 提供部分支持，需要加上前缀 -webkit-
 - Chrome for Android 42 以上版本

需要注意的地方是 Android 4.1-4.3 自带浏览器内核版本为 WebKit 534，也就是说 WebKit 534 （或更低版本）的浏览器内核对 Flexbox 的支持也不是很完善，例如 QQ 的 X5 引擎等。

## Flexbox 名词

Flexbox 是布局模块，包含父元素和子元素的属性。其中模型主要涉及了这些名词：

 - 主轴和侧轴
 - 主轴方向和侧轴方向
 - 主侧轴的起点和终点
 - 主侧轴的长度和长度属性

 像下面这样的图会更容易理解一些：

 ![flexbox 名词解释][http://img.blog.csdn.net/20150614222502311]

## 应用场景

### SegmentFault 的应用示例

 1.水平竖直居中

 以往在我做竖直居中的时候更多地采用 table-cell 和 vertical-align:middle; 的属性来实现，而现在 flexbox 布局可以很方便的解决这个问题。

 **实现方法：设置父元素 display:flex; ，子元素 margin:auto; 即可实现完全居中。**

 2.子元素布局随浏览器大小改变

 在一个容器内排布 6 个 子元素，子元素的布局会随着浏览器大小的变动而变动。

 **实现方法：父元素设置 display: flex; flex-flow:row wrap; justify-content: space-around; 即可。**

## Flexbox CSS 相关属性

这里只根据个人开发需要整理出了几个常用的属性。如果想不起来改用哪一个，可以查阅一下![这里](https://segmentfault.com/a/1190000002910324#articleHeader5)

#### flex-container （父元素）的 display 属性

与 Flexbox 布局相关的主要有以下两个值:

 - flex
 - inline-flex

#### 父元素的 flex-direction 属性

主要有以下的值:

 - row（默认），从左向右
 - row-reverse，从右向左（reverse 是反转的意思）
 - column，从上到下
 - column-reverse，从下到上

#### 父元素的 flex-wrap 属性

定义容器的子元素溢出时如何显示。主要有以下的值：

 - nowrap（默认），单行显示
 - wrap，多行显示
 - wrap-reverse，多行显示，方向与 wrap 相反

*PS：可以把父元素的 flex-direction 和 fiex-wrap 一起写在属性 flex-flow 里，像这样 : *

```
/* use flex-flow */
flex-flow : row nowrap;

/* the same as use flex-direction and flex-wrap */
flex-direction: row;
flex-wrap: nowrap;
```

#### 父元素的 justify-content 属性

justify 是对齐的意思，分配子元素伸缩后仍多出来的空间。主要有下面的值：

 - flex-start，默认，向起始位置靠齐
 - flex-end，这个就是向结束位置靠齐辣
 - center，顾名思义就是向中间靠齐的意思啦
 - space-between，将空位平均分给每个相邻元素的地方~
 - space-around，刚才在 6个元素布局 的时候用过，元素的两端都会保留相等的两段空间

#### flex-item（子元素）的 order 属性

可以控制子元素在父元素中的出现顺序，如果没有设置默认是按照代码里的顺序先后排列的。值应该是一个整数。

#### align-content 和 align-items

align-content 和 align-items 的属性值与 justify-content 的相似，不同的地方是多了一个叫做 stretch（拉伸） 的属性值，这是 align-items 的默认值，伸缩子元素以填满整个容器。除此之外，align-items 还有一个 baseline 的属性值，用于伸缩项目根据基线对齐。

#### 其他属性

 - flex-grow
 - align-self
 - flex-shrink
 -flex-basis
 - flex (for flex item)

 Copyright(c) 2016 MoeFront Studio