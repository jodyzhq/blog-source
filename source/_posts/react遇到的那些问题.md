---
title: react遇到的那些问题
date: 2017-03-08 22:37:04
categories:
- 技术
- React
tags: React
---

### 1.React创建自定义属性及引用自定义属性的方法

React在给标签创建自定义属性的方式不能简单的定义一个如row={3}这样的属性. 你会发现创建完虽然不报错,但根本取不到row
<!-- more -->
正确的做法是, 将属性以data-开头,即定义为: data-row={3}. 这样在获取数据的时候才能通过target.dataset或target.attributes看到数据. 如图:
![](/css/images/react1.png)

大家可以看到, 定义成data-row的属性, 在attributes里是data-row, 在dataset里是row.

这个时候有经验的开发人员就应该知道怎么来引用自定义属性了.

下面贴出一个例子:
下面这是react中的自定义属性

```html
<div data-row={curLine} data-col={curCol} ></div>
```
下面这是react的某个方法中的调用自定义属性的js代码段:

```javascript
var row = ev.target.getAttribute('data-row');
var col = ev.target.getAttribute('data-col');
```