---
title: CSS3中的clip-path使用攻略
date: 2017-02-18 17:52:30
categories: 
  - 技术
  - CSS
tags: CSS3
---
利用clip-path，我们可以创建圆形、椭圆和多边形等不同的形状，创造力是唯一的限制。
clip-path之所以没有很普及，是因为其浏览器兼容问题。很多IE浏览器对齐属性不是很支持。我们看下他的浏览器兼容：
<!-- more -->
![](/css/images/clip_jr.png)

我们看到IE是完全不支持，尽量使用webkit内核，需要加上内核前缀-webkit-

好了，进入正题来创建几个图形吧！



```css
//先加载张图片
.clip{
      background: url(images/clip.png) no-repeat;
      width: 500px;
      height: 500px;
}
```
#### 效果如下：
![](/css/images/clip0.png)


#### 一个简单的三角形创建：
```css
.clip-polygon {
　-webkit-clip-path: polygon(0 100%, 50% 0, 100% 100%);
}
```

#### 效果如下：
![](/css/images/clip1.png)

逐步分析
很像定位属性，我们需要考虑X值和Y值。X:0和Y:0表示从元素的左上角开始，并从左上角开始移动。X:100%指的是元素右边，Y:100%指的是元素底部。
对于上面创建的路径，实际是创建了如下的点：
x: 0, y:100%
x: 50%, y: 0
x: 100%, y: 100%
这个简单路径开始于左下角，水平移动50%，并到达顶部位置，然后又水平移动到100%的位置，垂直向下回到底部，到达第三个坐标点。三角形就出来了。

#### 创建一个圆形
需要给circle传入三个值：圆心的坐标(X值和Y值)以及半径。当定义圆的半径时，我们可以用at关键字来定义圆心坐标。
```css
.clip-circle {
　-webkit-clip-path: circle(50% at 50% 50%);
}
```

#### 效果如下：
![](/css/images/clip2.png)

#### 创建一个椭圆
椭圆需要给ellipse提供4个值：椭圆的x轴半径、y轴半径、定位椭圆位置的x坐标和y坐标，后面两个值用at关键字和前面两个值分开
```css
.clip-ellipse {
　-webkit-clip-path: ellipse(30% 20% at 50% 50%);
}
```

#### 效果如下：
![](/css/images/clip3.png)


#### 创建圆角矩形
圆角矩形需要给Inset四个值(对应“上 右 下 左”的顺序)来设置圆角半径。

```css
.clip-inset {
  　-webkit-clip-path: inset(25% 0 25% 0 round 0 25% 0 25%);
    -webkit-clip-path: inset(25% 0 25% 0 round 0 25% 0 25%);
}
```
#### 效果如下：
![](/css/images/clip4.png)

#### 创建一个复杂图形
使用polygon来 创建

```css
.clip-polygon {
  -webkit-clip-path: polygon(0% 0%, 100% 0%, 100% 75%, 75% 75%, 75% 100%, 50% 75%, 0% 75%);
｝
```
#### 效果如下：
![](/css/images/clip5.png)

好了，图形创建就到这里吧，使用polygon可以创建出任意你好要的图形
