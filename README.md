# brave
just do it


* {
*  
* }
* box-sizing 介绍（http://blog.sina.com.cn/s/blog_877284510101kt87.html）
*  box-sizing语法：


  box-sizing ： content-box || border-box || inherit

 

取值说明

1、content-box:此值为其默认值，其让元素维持W3C的标准Box Model，也就是说元素的宽度/高度（width/height）等于元素边框宽度（border）加上元素内边距（padding）加上元素内容宽度/高度（content width/height）即：Element Width/Height = border+padding+content width/height。

2、border-box:此值让元素维持IE传统的Box Model（IE6以下版本），也就是说元素的宽度/高度等于元素内容的宽度/高度。（从上面Box Model介绍可知，我们这里的content width/height包含了元素的border,padding,内容的width/height【此处的内容宽度/高度=width/height-border-padding】）
