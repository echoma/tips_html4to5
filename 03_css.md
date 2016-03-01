# CSS3的大量改进

## 新的选择器

##### 选择器是什么？

* 方便在针对某类符合指定规则的元素编写样式
* 常用的`.class` `#id`都是css-1选择器

```css
	.black {color:black;}	/*class为black的元素，前景色为黑色*/
    #name {border:1px solid black;}		/*id为name的元素加黑色边框*/
```

* 类似`*` `:focus` `[attr]`都是css-2选择器

```css
	* {font-size:14px;}		/*所有元素的字号为14像素*/
	:focus {border:1px solid blue;}		/*所有输入框拥有焦点时加蓝色边框*/
    [sort=odd] {background-color: gray;}	/*所有sort属性是odd的元素，背景色为灰色*/
```

##### 几类新增的css3选择器

* 遍历型：在元素遍历过程中进行选择

| 选择器 | 例子 | 描述 |
| ------ | ------ | ------ |
| element1~element2 | p~ul | 前面有`<p>`与阿奴的每个`<ul>`元素 |
| [attribute^=value] | a[src^="https"] | 选择其 src 属性值以 "https" 开头的每个`<a>`元素。 |
| :nth-child(n) | p:nth-child(2) | 选择属于其父元素的第二个子元素的每个`<p>`元素。 |

* 用户交互型：根据用户的行为做响应（类似以前的`:focus`）

| 选择器 | 例子 | 描述 |
| ------ | ------ | ------ |
| :enabled | input:enabled | 选择每个启用的`<input>`元素。 |
| ::selection | ::selection | 选择被用户选取的元素部分。 |
| :checked | input:checked | 选择每个被选中的`<input>`元素。 |

* 完整的选择器列表：http://www.w3school.com.cn/cssref/css_selectors.ASP

* 在js脚本里使用DomElement.querySelector()，可以动态的运行选择器。可以作为jquery选择器的一种本地替代方案。

## 颜色支持透明度

所有指定颜色的地方都可以指定透明度了

```html
<div class="a"></div>
<div class="b"></div>
```

```css
div {width:100px;height:100px;}
div.a { background: rgba(200,54,54,0.5); }
div.b { background: rgba(54,54,200,0.5); position:absolute; left:50px; top:50px; }
```

## 新增的实用视觉样式

* 圆角边框 `border-radius: length|percentage`

```html
	<div style="border: 10px solid; border-radius: 10px">
    	some text some text some text some text<br/>
        some text some text some text some text<br/>
        some text some text some text some text
    </div>
```

* 文字投影 `text-shadow: offset-x offset-y blur-radius color`

```html
    <p>Sed ut perspiciatis unde omnis iste natus</p>
    <p style="text-shadow: 1px 1px 1px gray;">
       Sed ut perspiciatis unde omnis iste natus
    </p>
    <p style="text-shadow: 1px 1px 2px black, 0 0 1em blue, 0 0 0.2em blue;">
       Sed ut perspiciatis unde omnis iste natus
    </p>
```

* 盒子投影 `box-shadow: offset-x | offset-y | blur-radius | color`

```html
    <div style="box-shadow: 10px 10px 5px gray; width:100px; height:100px; border: 1px solid black;">
    Sed ut perspiciatis unde omnis iste natus
    </div>
```

* 背景渐变 `background-image: linear-gradient(to bottom, blue, pink);`

```html
	<div style="width:100px;height:100px;background-image: linear-gradient(to bottom, blue, pink);">
    	Sed ut perspiciatis unde omnis iste natus
    </div>
    <div style="background: repeating-radial-gradient(#b8e7bf, #b8e7bf 5px, white 5px, white 10px); width:100px; height:100px;">
    	Sed ut perspiciatis unde omnis iste natus
    </div>
```

* 透明颜色和这些使用的视觉样式相配合，可以省掉大量的图片，大大提高页面的加载速度

## 属性取值可动态计算

* 新增calc()函数，动态计算属性的取值，省略了大量的脚本

```html
<div class="banner">This is a banner!</div>
```

```css
.banner {
  position: absolute;
  left: 5%;                 /* fallback for browsers without support for calc() */
  left: 40px;
  width: 90%;               /* fallback for browsers without support for calc() */
  width: calc(100% - 80px);
  border: solid black 1px;
  box-shadow: 1px 2px;
  background-color: yellow;
  padding: 6px;
  text-align: center;
}
```

## 变形和动画