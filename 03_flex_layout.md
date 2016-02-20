# 弹性布局

## 弹性布局是

* 一套全新的布局思路
* 一组CSS属性

## 原来的布局方案有什么问题？

传统的布局方案是这样的：

* HTML默认是流式排版：把元素从左向右，从上到下依次排开。
* 配合CSS, 使用浮动、绝对定位和相对定位满足非流式的布局需求

传统布局方案的问题是： **太他妈难调了！**

![css2就是一坨shit](./assert/03/css_shit.gif)

## 弹性布局的优点

* 全新的布局思路，更符合正常人的思维，能够自然的描述布局，例如：
  + a. 这个对话框里的内容分为左中右三块，左边为固定的200像素宽，剩下的部分按1:2划分。
  + b. 这个编辑器要撑满浏览器，随着浏览器大小变化，分为上下两块，上边是固定50像素高的工具条，下边是一个编辑框。

* 空间计算能力强，可伸缩，具有弹性。

## 如何简单描述一个弹性容器

* 概念较多

##### 容器的基本定义

* 这个元素作为一个容器，其内部的元素使用弹性布局。
  + `display: flex;`

* 主轴方向：容器内部的元素按照水平（从左到右 或 从右到左）或垂直方向（从上到下 或 从下到上）排列。
  + ![主轴方向](./assert/03/flex_direction.svg)
  + `flex-direction: row | row-reverse | column | column-reverse`
  + 容器主轴的头和尾
  + 容器侧轴的头和尾
  + ![头尾](./assert/03/flex_start_end.jpg)

##### 容器内部的固定大小元素的排列规则

* 如果容器在主轴排满了，是否可以换行。
  + ![换行](./assert/03/flex_wrap.svg)
  + `flex-wrap: nowrap | wrap | wrap-reverse`

* 主轴对齐：容器内部的元素在主轴方向上的对齐方式是怎样的。（头对齐、尾对齐、居中、散列、顶头散列）
  + `justify-content: flex-start | flex-end | center | space-between | space-around;`
  + ![主轴对齐](./assert/03/justify_content.svg)

* 侧轴对齐：
  + `align-items: flex-start | flex-end | center | baseline | stretch;`
  + ![侧轴对齐](./assert/03/align_items.svg)

* 如果有换行，测轴方向剩余空间的使用规则
  + `align-content: flex-start | flex-end | center | space-between | space-around | stretch;`
  + ![换行侧轴空白](./assert/03/align_content.svg)

##### 容器内部的弹性大小元素的尺寸计算规则

##
* ：该元素作为一个容器，其内部的元素使用弹性布局
* 