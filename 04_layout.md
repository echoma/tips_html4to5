# 弹性布局

弹性布局是一套全新的布局思路，包含了一组CSS属性

## 原来的布局方案有什么问题？

传统的布局方案是这样的：

* HTML默认是流式排版：把元素从左向右，从上到下依次排开。
* 配合CSS, 使用浮动、绝对定位和相对定位满足非流式的布局需求

传统布局方案的问题是： **太他妈难调了！**

![css2就是一坨shit](./assert/04/css_shit.gif)

## 弹性布局的优点

* 全新的布局思路，更符合正常人的思维，能够自然的描述布局，例如：
  + a. 这个对话框里的内容分为左中右三块，左边为固定的200像素宽，剩下的部分按1:2划分。
  + b. 这个编辑器要撑满浏览器，随着浏览器大小变化，分为上下两块，上边是固定50像素高的工具条，下边是一个编辑框。

* 空间计算能力强，可伸缩，具有弹性。

## 如何简单描述一个弹性容器

##### 容器的基本定义

* 这个元素作为一个容器，其内部的元素使用弹性布局。
  + `display: flex;`

* 主轴方向：容器内部的元素按照水平（从左到右 或 从右到左）或垂直方向（从上到下 或 从下到上）排列。
  + ![主轴方向](./assert/04/flex_direction.jpg)
  + `flex-direction: row | row-reverse | column | column-reverse`
  + 容器主轴的头和尾
  + 容器侧轴的头和尾
  + ![头尾](./assert/04/flex_start_end.jpg)

##### 容器内部的固定大小元素的排列规则

* 如果容器在主轴排满了，是否可以换行。
  + ![换行](./assert/04/flex_wrap.jpg)
  + `flex-wrap: nowrap | wrap | wrap-reverse`

* 主轴对齐：容器内部的元素在主轴方向上的对齐方式是怎样的。（头对齐、尾对齐、居中、散列、顶头散列）
  + `justify-content: flex-start | flex-end | center | space-between | space-around;`
  + ![主轴对齐](./assert/04/justify_content.jpg)

* 侧轴对齐：
  + `align-items: flex-start | flex-end | center | baseline | stretch;`
  + ![侧轴对齐](./assert/04/align_items.jpg)

* 如果有换行，测轴方向剩余空间的使用规则
  + `align-content: flex-start | flex-end | center | space-between | space-around | stretch;`
  + ![换行侧轴空白](./assert/04/align_content.jpg)

##### 容器内部的弹性元素的尺寸计算规则

* 元素将如何增大自己的尺寸
  + `flex-grow: <number>; /* default 0 */`
  + ![增大尺寸](./assert/04/flex_grow.jpg)

* 元素将如何压缩自己的尺寸
  + `flex-shrink: <number>; /* default 0 */`

* 元素的初始尺寸
  + `flex-basis: <length> | auto; /* default auto */`

* 组合：
  + `flex: none | [ <'flex-grow'> <'flex-shrink'>? || <'flex-basis'> ]`

## 参考文章

* 英文 https://css-tricks.com/snippets/css/a-guide-to-flexbox/
* 中文 http://www.w3cplus.com/css3/a-guide-to-flexbox.html

## 实际例子

![微信截图](./assert/04/weixin_snap.jpg)

[codepen的代码地址](http://codepen.io/anon/pen/gPVjmg)

##### 整体结构

* 整体分为上中下三块

```html
<div class="main">
  <div class="top">顶部导航</div>
  <div class="cet">聊天内容</div>
  <div class="bot">底部输入框</div>
</div>
```

```css
*{font-size:14px; color:white; }
html, body{height:100%; margin: 0px; }

.main{height:100%; display:flex; flex-direction: column; background:lightgray; }
.top{height:30px; background:black;padding: 5px; }
.bot{height:50px; background:black;padding: 5px; }
.cet{flex:1;font-size:12px; color:black; padding: 5px; }
```

* 顶部导航部分分为左中右三块（回退、人名、菜单），因此内容变为

```html
<div class="main">
  <div class="top">
    <div class="lef">&lt;微信</div>
    <div class="cet">圆圆</div>
    <div class="rig">人头</div>
  </div>
  <div class="cet">聊天内容</div>
  <div class="bot">底部输入框</div>
</div>
```

```css
*{font-size:14px; color:white; }
html, body{height:100%; margin: 0px; }

.main{height:100%; display:flex; flex-direction: column; background:lightgray; }
.top{height:30px; background:black;padding: 5px; display:flex;flex-direction: row;}
.top .lef{width:50px; margin:5px;}
.top .rig{width:50px; margin:5px;}
.top .cet{flex:1; font-size:18px; color:white;text-align:center;}
.bot{height:50px; background:black;padding: 5px; }
.cet{flex:1;font-size:12px; color:black; padding: 5px; }
```

* 底部输入框也是左中右三部分（语音输入按钮、文字输入框、两个按钮），因此内容变为：

```html
<div class="main">
  <div class="top">
    <div class="lef">&lt;微信</div>
    <div class="cet">圆圆</div>
    <div class="rig">人头</div>
  </div>
  <div class="cet">聊天内容</div>
  <div class="bot">
    <button class="lef">0</button>
    <input class="cet" type="text">
    <button class="rig">1</button>
    <button class="rig">2</button>
  </div>
</div>
```

```css
*{font-size:14px; color:white; }
html, body{height:100%; margin: 0px; }

.main{height:100%; display:flex; flex-direction: column; background:#999; }

.top{height:30px; background:black;padding: 5px; display:flex;flex-direction: row;}
.top .lef{width:50px; margin:5px;}
.top .rig{width:50px; margin:5px;}
.top .cet{flex:1; font-size:18px; color:white;text-align:center;}

.bot{height:30px; background:lightgray; padding: 5px; display:flex;flex-direction: row;}
.bot button{width:25px; height:25px; margin:5px;border-color:black; border-radius:10px;color:black;}
.bot .cet{flex:1; font-size:18px; color:white;text-align:center;border-radius:5px;}

.cet{flex:1;font-size:12px; color:black; padding: 5px; }
```

* 中间消息列表其实就是一个主轴方向为`纵向`的弹性布局，即`flex-direction:column`
* 每一条消息其实就是分为两部分，一个头像，一个消息内容。自己发的是头像在左，对方法的头像在右，这正好用`flex-direction:row-reverse`来实现

```html
<div class="main">
  <div class="top">
    <div class="lef">&lt;微信</div>
    <div class="center">圆圆</div>
    <div class="rig">人头</div>
  </div>
  <div class="cet">
    <div class="msg send">
      <div class="avata"></div>
      <div class="content">放假一起去旅游吧</div>
    </div>
    <div class="msg recv">
      <div class="avata"></div>
      <div class="content">好啊期待很久了</div>
    </div>
  </div>
  <div class="bot">
    <button class="lef">0</button>
    <input class="center" type="text">
    <button class="rig">1</button>
    <button class="rig">2</button>
  </div>
</div>
```

```css
*{font-size:14px; color:white; }
html, body{height:100%; margin: 0px; }

.main{height:100%; display:flex; flex-direction: column; background:#999; }

.top{height:30px; background:black;padding: 5px; display:flex;flex-direction: row;}
.top .lef{width:50px; margin:5px;}
.top .rig{width:50px; margin:5px;}
.top .center{flex:1; font-size:18px; color:white; text-align:center;}

.bot{height:30px; background:lightgray; padding: 5px; display:flex;flex-direction: row;}
.bot button{width:25px; height:25px; margin:5px;border-color:black; border-radius:10px;color:black;}
.bot .center{flex:1; font-size:18px; color:white;text-align:center;border-radius:5px;}

.cet {flex:1;font-size:12px; color:black; padding: 5px; display:flex; flex-direction:column; overflow-y:scroll;}
.cet .msg{display:flex; margin:10px; align-items: flex-start}
.cet .msg .avata {border:1px solid gray; width:60px; height:60px; background-color: white;}
.cet .msg .content {border:1px solid gray; margin:0 10px; padding: 10px; background-color: lightgray; color:black; }
.cet .recv {flex-direction:row-reverse;}
```

# 多列布局

多列布局常见于报刊杂志等读物。包含了两个CSS属性:

* column-count: 内容要分几列。自动计算每列宽度。
* column-width: 没一列内容的宽度。自动计算列数。

```html
<div class="sample">多年以后，奥雷连诺上校站在行刑队面前，准会想起父亲带他去参观冰块的那个遥远的下午。当时，马孔多是个二十户人家的村庄，一座座土房都盖在河岸上，河水清澈，沿着遍布石头的河床流去，河里的石头光滑、洁白，活象史前的巨蛋。这块天地还是新开辟的，许多东西都叫不出名字，不得不用手指指点点。每年三月，衣衫褴楼的吉卜赛人都要在村边搭起帐篷，在笛鼓的喧嚣声中，向马孔多的居民介绍科学家的最新发明。他们首先带来的是磁铁。一个身躯高大的吉卜赛人，自称梅尔加德斯，满脸络腮胡子，手指瘦得象鸟的爪子，向观众出色地表演了他所谓的马其顿炼金术士创造的世界第八奇迹。他手里拿着两大块磁铁，从一座农舍走到另一座农舍，大家都惊异地看见，铁锅、铁盆、铁钳、铁炉都从原地倒下，木板上的钉子和螺丝嘎吱嘎吱地拼命想挣脱出来，甚至那些早就丢失的东西也从找过多次的地方兀然出现，乱七八糟地跟在梅尔加德斯的魔铁后面。“东西也是有生命的，”吉卜赛人用刺耳的声调说，“只消唤起它们的灵性。”霍·阿·布恩蒂亚狂热的想象力经常超过大自然的创造力，甚至越过奇迹和魔力的限度，他认为这种暂时无用的科学发明可以用来开采地下的金子。</div>
```

```css
.sample {width:500px; column-count:2; -webkit-column-count: 2;}
```