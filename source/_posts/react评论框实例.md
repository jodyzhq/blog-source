---
title: react评论框实例
date: 2017-02-20 21:58:41
tags:
---

我们将建立一个你可以放进博客的简单却真实的评论框，一个 Disqus、LiveFyre 或 Facebook comments 提供的实时评论的基础版本。
<!-- more -->
我们将提供：

一个所有评论的视图
一个用于提交评论的表单
为你提供制定后台的挂钩(Hooks)
同时也会有一些简洁的功能：

优化的评论： 评论在它们保存到服务器之前就显示在列表里,所以感觉很快。
实时更新： 其他用户的评论被实时浮现到评论中。
Markdown格式化： 用户可以用Markdown格式化它们的文字。
想要跳过所有内容，只查看源代码？
全在 GitHub .

运行服务器
为了开始本教程，我们将要需要一个运行着的服务器。这将是我们纯粹用来获取和保存数据的伺服终端。为了让这尽可能的容易，我们已经用许多不同的语言编写了简单的服务器，它正好完成我们需要的事。 你可以查看源代码 或者 下载 zip 文件 包括了所有你开始学习需要的东西

为了简单起见，我们将要运行的服务器使用 JSON 文件作为数据库。你不会在生产环境运行这个，但是它让我们更容易模拟使用一个API时你可能会做的事。一旦你启动服务器，它将会支持我们的API终端,同时也将伺服我们需要的静态页面。

### 开始
对于此教程,我们将使它尽可能的容易。被包括在上面讨论的服务器包里的是一个我们将在其中工作的 HTML 文件。在你最喜欢的编辑器里打开 public/index.html。它应该看起来像这样 （可能有一些小的不同，稍后我们将添加一个额外的 <code> script </code> 标签）：

```html
<!-- index.html -->
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8" />
    <title>React Tutorial</title>
    <script src="https://npmcdn.com/react@15.3.1/dist/react.js"></script>
    <script src="https://npmcdn.com/react-dom@15.3.1/dist/react-dom.js"></script>
    <script src="https://npmcdn.com/babel-core@5.8.38/browser.min.js"></script>
    <script src="https://npmcdn.com/jquery@3.1.0/dist/jquery.min.js"></script>
    <script src="https://npmcdn.com/remarkable@1.6.2/dist/remarkable.min.js"></script>
  </head>
  <body>
    <div id="content"></div>
    <script type="text/babel" src="scripts/example.js"></script>
    <script type="text/babel">
      // To get started with this tutorial running your own code, simply remove
      // the script tag loading scripts/example.js and start writing code here.
    </script>
  </body>
</html>

```

在本教程剩余的部分，我们将在此 script 标签中编写我们的 JavaScript 代码。我们没有任何高级的实时加载所以在保存以后你需要刷新你的浏览器来观察更新。通过在浏览器打开 http://localhost:3000 关注你的进展。当你没有任何修改第一次加载时，你将看到我们将要准备建立的已经完成的产品。当你准备开始工作，请删除前面的 <script> 标签然后你就可以继续了。

注意：
我们在这里引入 jQuery 是因为我们想简化我们未来的 ajax 请求，但这对React的正常工作 不是 必要的。

