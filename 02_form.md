# 表单的大量改进

## 输入焦点的控制

* 全局tabindex属性灵活控制按下tab键的焦点跳转顺序。
  + `>0`的值，将从小到大依次跳转；
  + `=0`的值，在`>0`的跳转完后按照出现顺序跳转；
  + `<0`的值，不会被跳转。

* autofocus属性自动获取输入焦点。不再需要使用js脚本在页面加载完成的事件里取控制了。

```html
    <form>
      <input placeholder=tabindex是3 tabindex=3 />
      <input placeholder=tabindex是1 tabindex=1 autofocus />
      <input placeholder=tabindex是0 tabindex=0 />
      <input placeholder=tabindex是2 tabindex=2 />
      <input placeholder=tabindex是-1 tabindex=-1 />
    </form>
```

## 表单控件可以位于`<form>`标签之外

* 老的HTML4时代：
```html
    <!-- 所有控件必须在<form>元素内部，导致描述页面布局还要考虑控件和<form>的从属关系 -->
    <!-- 经常碰到蛋疼的问题：调整页面结构和布局的时候，老是要把<form>的位置调来调去 -->
    <form>
    <input type=text name=email/>
    </form>
```

* HTMl5时代:
```html
    <!-- 控件可以脱离<form> -->
    <form id=1></form>
    <input form=1 type=text name=email/>
```

## 输入控件新增大量类型(type属性)

* 之前用复杂的脚本才能实现的颜色拾取器、日期选择器、范围选择器现在直接用简单的html5代码就可以实现了。

```html
	<input type="color"/> <!-- 颜色拾取 -->
    <input type="date"/> <!-- 日期选择 -->
    <input type="datetime-local"/> <!-- 日期及时间选择 -->
    <input type="range"/> <!-- 范围选择 -->
```

* 之前需要用脚本来限定用户输入内容的情况，某些常用的限定条件也可以用html5来简单实现。

```html
	<form>
	<input type=email/> <!-- 邮箱 -->
    <input type=number/> <!-- 数字 -->
    <input type=url/> <!-- 链接 -->
    <input type=submit value=提交 />
    </form>
```

## 输入控件新增大量新属性

* required属性：该输入框必填。

```html
    <form>
      <input placeholder=这里必填 required/>
      <input placeholder=这里选填 />
      <button>提交</button>
    </form>
```

* placeholder属性：该输入框未填写时的提示语

```html
	<input type=email placeholder="Input Your Email" />
```

* pattern属性：使用正则表达式限定可以输入的内容

```html
	<form>
		<input type=text pattern="[a-c]+" />
    	<button>提交</button>
    </form>
```

* min/max/step属性：对于数字输入框，限定范围和变化步幅

```html
	<form>
		<input type=number min=5 max=20 step=3 />
        <input type=range min=5 max=20 step=3 />
        <button>提交</button>
    </form>
```

* maxlength/minlength属性：该输入框内容的最大最小字数

```html
	<form>
		<input type=text maxlength=10 minlength=5 />
        <button>提交</button>
    </form>
```

* list属性：配合datalist元素实现ComboBox

```html
    <input list=browsers />
    <datalist id=browsers>
      <option value="Chrome">
      <option value="Firefox">
      <option value="Internet Explorer">
      <option value="Opera">
      <option value="Safari">
    </datalist>
```

* multiple属性：配合file类型的输入框实现文件多选，配合email类型的输入框实现多个email输入

```html
	<form>
        <input type=file multiple />
        <input type=email multiple /> <!-- 多个email之间用逗号隔开 -->
        <button>提交</button>
    </form>
```

* 更多内容可以参考[这个页面](https://developer.mozilla.org/en/docs/Web/HTML/Element/Input)

## 按钮`<button>`

* 不同于`<input>`的button类型，`<button>`作为一种常规html元素，可以内嵌各种html和使用各种样式。
* 也可以有`type`属性： submit, reset, button，分表表示提交表单、重置表单、普通按钮
* 也可以有autofocus和form属性

```css
.sample {color:#fff,background-color:#2b6090; border-color:#204d74; padding:6px 12px; text-align:center; }
.sample:hover {background-color:#000;}
```
```html
<button>无样式</button>
<button class=sample>有样式</button>
```