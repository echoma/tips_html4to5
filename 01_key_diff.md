# HTML5的主要变化

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

## 大量的新元素

* 例如： article, aside, audio, bdi, canvas, command, data, datalist, details, embed, figcaption, figure, footer, header, keygen, mark, meter, nav, output, progress, rp, rt, ruby, section, source, summary, time, track, video, wbr
* 使用新元素对页面内容进行语义描述，方便对搜索引擎的优化
* 不少新元素也对网页的功能做了扩展，如audio, video

## 表单的大量改进

##### 表单<form>可以仅作为逻辑控制标签

* H4:
```html
    <!-- 所有空间必须在form标签内部，导致描述页面布局还要考虑控件和form的从属关系 -->
    <form>
    <input type=text name=email/>
    </form>
```

* H5:
```html
    <!-- 控件可以脱离form -->
    <form id=1>
    <input form=1 type=text name=email/>
    </form>
```

##### 大量的控件改进

* 输入框&lt;input&gt;的type属性新增大量可取值;
* 使用&lt;datalist&gt;配合&lt;input&gt;可以轻松实现combobox;
* 全局tabindex控制tab顺序，和autofocus属性自动获取输入焦点;
* required属性表示该属性必填;
* 这些改进都会在[02_form.md](02_form.md)里讲述。

## 更加方便WebApp的开发

* 多媒体标签： audio和video标签嵌入音视频流
* 地理位置API： 可调用设备的GPS进行定位
* 本地存储：WebSQL提供了本地的key/value数据库
* 与服务器实时通信： WebSocket在TCP上层封装了基于消息的通信机制
* 桌面通知： NotificationAPI提供了向操作发送通知消息的能力
* 画布： canvas和绘图API，拥有了flash的能力
* 这些改进都会在[04_webapp.md](04_we.md)里讲述。