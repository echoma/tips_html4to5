# CSS实用工具：FontFace和SASS

## FontFace

##### 它是什么？

一个css3新属性，让我们可以在网页上使用自定义字体的方案。

##### 它能解决哪些问题？

* 要在网页中使用非常美观的自定义字体要做成图片，这种方案导致网页加载慢、字体复用程度低，且通常不是矢量图案。

* 网页中大量的小图标通常使用叫做Sprite的技术（所有图标被绘制到到一张图片上并加载，前端要显示某个图标时根据像素定位显示图片的指定部位），这种方案调整像素比较复杂，使用局限性也很多，且通常不是矢量图案。

##### 它如何解决问题的？

* 作为一种字体，它首先可以是矢量的，字体的可复用性比图片要好很多，可以随意使用，而且可以方便结合其他CSS属性使用，更加灵活。

* 对于小图标，每种图标都可以对应字体里的某一个字，在HTML内容里输入某个字，就可以显示为对应的图标。这种技术被称作FontIcon，比传统的Sprite更加灵活，更易于使用，可以方便的搭配各种CSS属性使用（尺寸、颜色、透明度）。

##### 如何使用？

* 首先需要一个字体。

  - 网络上有大量开源的图标字体，最著名的是[FontAwesome](https://fortawesome.github.io/Font-Awesome/)，它包含了600多种常用的矢量图标，而且还预设了一组CSS，方便对图标进行各种变形和动画。

  - 网上也有大量免费的字体生成工具，可以使用任意预设的图标和自己上传的图标组成生成一个字体。比较著名的有[IcoMoon](https://icomoon.io/app/#/select)，预设了大量免费图标，可以生成svg、ttf、woff三种格式的字体.

  - 如果要自己绘制矢量图标，可以使用专业软件，比如Illustrator，可以绘制svg矢量图形。

* 使用css的font-face属性启用自定义字体。

  - 下面是一个从iconmoon上选择了4个预设图标生成的svg字体。

```css
    @font-face {
	font-family: 'icomoon';
	src: url('./icomoon.ttf') format('truetype');
	font-weight: normal;
	font-style: normal;
}
```

* 在html内容中使用字体。

```html
	<span style="font-family:'icomoon'">&#xe900</span>
	<button style="font-family:'icomoon'">&#xe901</button>
```

  - 由于带了自定义字体，这段代码无法在codepen上运行，可以下载[icomoon.html](./assert/05/icomoon.html)和[icomoon.ttf](./assert/05/icomoon.ttf)在本地运行。

## SASS

##### 它是什么？

它是一种CSS预处理器，为CSS引入了更多的编程特性，是的CSS更易于维护。[官网](http://sass-lang.com/)

##### 它能解决什么问题？

* CSS中大量的重复代码。有很多css类具有相同的属性或属性组合，经常要把这些属性在每个元素里都写一下。

* 经常为了改下颜色等属性，在样式文件里到处修改。

* 一些有层级关系的CSS类定义，要反复的书写各个类的层级关系。

* 很多CSS文件其实都有一些一样的定义，但为了加载速度，这些CSS定义还是在每份文件都写了一遍。

* 各浏览器有自己的css属性前缀，代码里总是写了各种各样的浏览器前缀。

##### 它如何解决问题之“变量”

* 先看一段例子代码

```css
$font: Helvetica, sans-serif, 宋体;
$color: #333;

body {
  font: 100% $font;
  color: $color;
}
```

* 这段代码使用SASS工具转换后会变成如下CSS代码

```css
body {
  font: 100% Helvetica, sans-serif, 宋体;
  color: #333;
}

```

* 只要想使用我们预定的某种字体组合和颜色的，就可以在样式中使用我们定义的变量。 之后只要修改变量的值，所有使用了这个变量的样式都会跟着变化字体和颜色。

##### 它如何解决问题之“嵌套”

* 下面这段代码

```css
nav {
  ul {
    margin: 0;
    padding: 0;
    list-style: none;
  }

  li { display: inline-block; }

  a {
    display: block;
    padding: 6px 12px;
    text-decoration: none;
  }
}

```

* 这段代码使用SASS工具转换后会变成如下CSS代码

```css
nav ul {
  margin: 0;
  padding: 0;
  list-style: none;
}

nav li {
  display: inline-block;
}
```

* 使用语法结构上的层级关系来描述CSS类的层级关系，这比之前的CSS语法更加自然，更好理解，也更好维护。

##### 它如何解决问题之“导入”

* 下面有两个SASS代码文件

```css
// _reset.scss

html,
body,
ul,
ol {
   margin: 0;
  padding: 0;
}
```

```css
// base.scss

@import 'reset';

body {
  font: 100% Helvetica, sans-serif;
  background-color: #efefef;
}
```

* 这段代码使用SASS工具转换后会变成如下CSS代码

```css
html, body, ul, ol {
  margin: 0;
  padding: 0;
}

body {
  font: 100% Helvetica, sans-serif;
  background-color: #efefef;
}
```

* 这使得多个CSS文件里相同的属性可以被提取到一个文件里来维护。

##### 它如何解决问题之“混合”

* 下面这段代码

```css
@mixin border-radius($radius) {
  -webkit-border-radius: $radius;
     -moz-border-radius: $radius;
      -ms-border-radius: $radius;
          border-radius: $radius;
}

.box { @include border-radius(10px); }
```

* 这段代码使用SASS工具转换后会变成如下CSS代码

```css
.box {
  -webkit-border-radius: 10px;
  -moz-border-radius: 10px;
  -ms-border-radius: 10px;
  border-radius: 10px;
}
```

* 这其实给CSS增加了函数的功能，可以使用参数生成一组CSS属性。上面的代码就用这个特性来解决各浏览器不同属性前缀的问题。

##### 还有其他好用的特性，可以自己在官网查看

* 还有类似于“类继承”、“属性运算”等好功能。

##### LESS

* 跟SASS类似，还有一个比较著名的CSS预处理器叫做LESS。他们的特性都差不多。LESS一个好处是它是Javascript编写的，可以在页面里动态的进行预处理。

* 官网：[less](http://lesscss.org/)