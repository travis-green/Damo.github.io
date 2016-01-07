---
layout: post
title: javascript DOM学习总结（二）
date: 2015-11-27
categories: blog
tags: [javascript]
description: 玩技术就要耐得住寂寞。

---

###获取和设置属性
**DOM**实在是个好东西，掌握了它我们不仅可以在JavaScript中使用，其它程序语言我们同样可以使用。
接下来就一起使用DOM来干些实事吧！
**1.getAttribute**
getAttribute是一个函数，它只有一个参数———就是我们要查询的属性的名字。
```
<!DOCTYPE html>
<html lang="en">
<head>
  <meta http-equiv="content-type" content="text/html; charset=utf-8" />
  <title>Test</title>
  <style></style>
</head>
<body>
  <p id="para" title="It's just a test !" >A example paragraph !</p>
  <script language="javascript">
     var para=document.getElementById("para")//利用getElementById获取id为para的元素
     var title=para.getAttribute("title");//获取title 属性
     alert(title);//弹出对话框 It's just a test !
  </script>
</body>
</html>
```
**截图：**

![这里写图片描述](http://img.blog.csdn.net/20151127155620521)
**说明：getAttribute函数只能得到属性却无法修改属性，如果我们要修改属性还得靠它：**

**2.setAttribute**
和getAttribute一样，setAttribute只能用于元素节点，setAttribute函数有两个参数，第一个是我们要修改的元素属性，第二个是我们要修改的内容，示例如下：
```
     var para=document.getElementById("para")//利用getElementById获取id为para的元素
     var title=para.setAttribute("title","Change title !");//修改title属性
     alert(para.title);//弹出Change title 
```
**截图：**

![这里写图片描述](http://img.blog.csdn.net/20151127160558878)

**当然DOM的属性和方法不仅仅是只有这几个，如nodeName,nodeValue,childNodes,nextSibling等，这里就举这几个人例子。**
#Happy hacking !
