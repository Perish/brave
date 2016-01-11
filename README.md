# brave
just do it


### box-sizing 介绍（http://blog.sina.com.cn/s/blog_877284510101kt87.html）
## box-sizing语法：
```css
  box-sizing ： content-box || border-box || inherit
```

取值说明

* content-box:此值为其默认值，其让元素维持W3C的标准Box Model，也就是说元素的宽度/高度（width/height）等于元素边框宽度（border）加上元素内边距（padding）加上元素内容宽度/高度（content width/height）即：Element Width/Height = border+padding+content width/height。

* border-box:此值让元素维持IE传统的Box Model（IE6以下版本），也就是说元素的宽度/高度等于元素内容的宽度/高度。（从上面Box Model介绍可知，我们这里的content width/height包含了元素的border,padding,内容的width/height【此处的内容宽度/高度=width/height-border-padding】）

### clearfix 清除浮动
```css
  .clearfix:before, .clearfix:after {
    content: " ";
    display: table;
  }
  .clearfix:after {
    clear: both;
  }
  .clearfix {
    *zoom: 1;
  }
```

### !important 优先级最高

```css
  .textClass {
    color: red !important;
  }
  .textClass {
    color: blue;
  }
```
上述中在textClass这个类包裹的文字颜色会是red

### transition 过渡效果

```css
  transition: [transition-property:属性] [transition-duration:变化时间] [transtion-time-function:时间函数] [transition-delay:延迟时间]
  
  div {
    -webkit-transition: background-color 0.5s ease;
    -moz-transition: background-color 0.5s ease;
    -o-transition: background-color 0.5s ease;
    transition: background-color 0.5s ease;
    background-color: red;
  }
  
  div:hover {
    background-color: green;
  }
```
### z-index 属性设置元素的堆叠顺序。拥有更高堆叠顺序的元素总是会处于堆叠顺序较低的元素的前面
注释：元素可拥有负的 z-index 属性值。
注释：Z-index 仅能在定位元素上奏效（例如 position:absolute;）！

```css 
  img {
      position:absolute;
      left:0px;
      top:0px;
      z-index:-1;
  }
```
