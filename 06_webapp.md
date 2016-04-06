# WebApp开发

HTML5/CSS3增加了大量新特性，以满足使用WEB技术开发桌面或移动应用的需要。

## 通知API

* 这是在javascript里新增的一套API，用于发送系统通知。对于Windows系统就是桌面右下角系统托盘区的气球消息。

* [API文档](https://developer.mozilla.org/en/docs/Web/API/notification)

```html
<button onclick="notifyMe()">Notify me!</button>
```

```javascript
function notifyMe() {
  // Let's check if the browser supports notifications
  if (!("Notification" in window)) {
    alert("This browser does not support desktop notification");
  }

  // Let's check whether notification permissions have already been granted
  else if (Notification.permission === "granted") {
    // If it's okay let's create a notification
    var notification = new Notification("Hi there!");
  }

  // Otherwise, we need to ask the user for permission
  else if (Notification.permission !== 'denied') {
    Notification.requestPermission(function (permission) {
      // If the user accepts, let's create a notification
      if (permission === "granted") {
        var notification = new Notification("Hi there!");
      }
    });
  }

  // At last, if the user has denied notifications, and you 
  // want to be respectful there is no need to bother them any more.
}
```

## WebSocket

* WebSocket是什么？
  + 一种通信新协议，让浏览器和服务器之间可以进行全双工、长连接的通信
  + 已经有IETF标准化为[RFC6455](http://tools.ietf.org/html/rfc6455)，因此也有各种主流语言的实现版本。

* WebSocket不是什么？
  + 它不是Socket。它是基于TCP/IP协议的，与HTTP、SMTP等协议并列的通信关系。
  + 不像HTTP那样规定了如何指定方法、目标资源、传递参数，WebSocket跟任何业务逻辑无关，它可以传输如何数据。

