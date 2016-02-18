# HTML5/CSS3的主要变化

## 文档基本格式比html4精炼很多：

* H4:
```html
    <!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN"
            "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
    <html xmlns="http://www.w3.org/1999/xhtml">
        <body></body>
    </html>
```

* H5:
```html
    <!doctype html>
    <html>
        <body></body>
    </html>
```

## 标准规定：属性值可以不用引号

```html
<span id=example></span>
```

## HTML更加纯粹

* HTML仅用来描述文档的语义结构，不在描述表现，表现由CSS负责
* 之前用来描述表现的元素已经不推荐使用，例如: `<b>`表示加粗, `<font>`表示使用字体。这些表现层面的东西要使用CSS来描述。
* 不要再使用`<table>`来控制布局了，它纯粹就是表示表格而已。CSS3还新增了弹性布局方案。
* 新增大量元素用来表示文档的语意结构： article, aside, audio, bdi, canvas, command, data, datalist, details, embed, figcaption, figure, footer, header, keygen, mark, meter, nav, output, progress, rp, rt, ruby, section, source, summary, time, track, video, wbr
* 使用新元素对页面内容进行语义描述，方便对搜索引擎的优化
* 不少新元素也对网页的功能做了扩展，例如多媒体支持：`<audio>`, `<video>`；绘图支持: `<canvas>`

## CSS更多新特性

* 选择器。jquery选择器的大部分功能其实可以用原生的css选择器来实现了。
* 更多的样式。像圆角、渐变色、投影都可以使用原生css来做了，不在需要图片了。
* 可针对多种屏幕尺寸编写样式，催生了响应式页面，一个页面可以同时适应桌面、手机、平板多种尺寸。
* 变形和动画支持。直接在css里定义动画，比原来js做动画的方式更方便，性能也更高。

## 表单的大量改进

* 表单内部的控件可以位于`<form>`标签的外部，不再受文档结构的局限
* 全局tabindex和autofocus轻松控制输入焦点
* 输入框`<input>`的type属性新增大量可取值;
* 使用`<datalist>`配合`<input>`可以轻松实现combobox;
* 全局tabindex控制tab顺序，和autofocus属性自动获取输入焦点;
* required属性表示该属性必填。

这些改进都会在[02_form.md](02_form.md)里讲述。

## 更加方便WebApp的开发

* 多媒体标签： audio和video标签嵌入音视频流
* 地理位置API： 可调用设备的GPS进行定位
* 本地存储：WebSQL提供了本地的key/value数据库
* 与服务器实时通信： WebSocket在TCP上层封装了基于消息的通信机制
* 桌面通知： NotificationAPI提供了向操作发送通知消息的能力
* 画布： canvas和绘图API，拥有了flash的能力

这些改进都会在[04_webapp.md](04_webapp.md)里讲述。