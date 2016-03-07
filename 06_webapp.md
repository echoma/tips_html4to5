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

* 