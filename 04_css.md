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

## 新增的实用视觉样式

* 圆角边框 `border-radius: length|percentage`

```html
	<div style="border: 10px solid; border-radius: 10px">
    	some text some text some text some text<br/>
        some text some text some text some text<br/>
        some text some text some text some text
    </div>
```

* 文字修饰 `text-shadow: offset-x offset-y blur-radius color`

```html
    <p>Sed ut perspiciatis unde omnis iste natus</p>
    <p style="text-shadow: 1px 1px 1px gray;">
       Sed ut perspiciatis unde omnis iste natus
    </p>
    <p style="text-shadow: 1px 1px 2px black, 0 0 1em blue, 0 0 0.2em blue;">
       Sed ut perspiciatis unde omnis iste natus
    </p>
```

* 背景渐变 `background-image: linear-gradient(to bottom, blue, pink);`

```html
	<div style="width:100px;height:100px;background-image: linear-gradient(to bottom, blue, pink);">
    	Sed ut perspiciatis unde omnis iste natus
    </div>
```