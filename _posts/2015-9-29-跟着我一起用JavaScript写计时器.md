###计时器小谈

对于刚刚接触JavaScript的小白来说，计时器好像是个特别高大上的东西，其实不然，JavaScript为我们提供了很多的API函数，我们只用这些API函数就足以写一个很好的计时器，当然写一个时钟肯定也不在话下了。

那么我们就一步步开始写计时器喽：

###1. 我们热热身

JavaScript脚本：
```
function timedMsg()
        {
            var t=setTimeout("alert('1 秒！')",1000)
        }        
```

HTML：
```
<form>
    <input type="button" value="显示定时的警告框" onClick = "timedMsg()">
</form>
<p>请点击上面的按钮。警告框会在 1 秒后显示。</p>
```

运行代码：

![结果](http://img.blog.csdn.net/20151120194238016)

**说明：这是一个简单的计时脚本，利用setTimeout函数使得警告框1秒后弹出。**

###2. 活动筋骨，有限计时

Javascript脚本：
```
  function timedText()
         {
         var t1=setTimeout("document.getElementById('txt').value='1 秒'",1000)
         var t2=setTimeout("document.getElementById('txt').value='2 秒'",2000)
         var t3=setTimeout("document.getElementById('txt').value='3 秒'",3000)
         }
```

HTML：
```
<form>
    <input type="button" value="显示计时的文本" onClick="timedText()">
    <input type="text" id="txt">
</form>
<p>点击上面的按钮。输入框会显示出已经逝去的时间（1、2、3 秒）</p>
```

运行代码：

![结果](http://img.blog.csdn.net/20151120194828615)

**说明：一个三秒的计时效果，当然和我们想象中的计时还有点差距。**

### 3. 无限计时

Javascript脚本：
```
   var c=0;事件
        function timedCount()
        {
            document.getElementById('txt').value=c
            c=c+1
            setTimeout("timedCount()",1000)
        }
```

HTML：
```
<form>
        <input type="button" value="开始计时！" onClick="timedCount()">
        <input type="text" id="txt">
    </form>
    <p>请点击上面的按钮。输入框会从 0 开始一直进行计时。</p>
```

运行代码：

![结果](http://img.blog.csdn.net/20151120195332371)

**说明：只要不关闭浏览器或是刷新网页，这个脚本就会一直运行下去，时间趋于无穷大。**

### 4. 货真价实的计时

脚本：
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <!--<style>
        #securityCode{
            background-color: #008000;
            width:70px;
            height:30px;
            font-family: '楷体', serif;
            font-size: 20px;
            color:white;
        }
    </style>-->
    <script language="JavaScript" type="text/javascript">
     var c=0;
        var t;
        function timedCount()
        {
            document.getElementById('txt').value=c;
            c=c+1;
            t=setTimeout("timedCount()",1000);
        }

        function stopCount()
        {
            setTimeout("document.getElementById('txt').value=c-1",0);
            clearTimeout(t);
        }
        function resetCount(){
            setTimeout("document.getElementById('txt').value=0",0);
            clearTimeout(t);
            c=0;
        }
            </script>
    <title>计时</title>
</head>
<body  >
<form>
    <input type="button" value="开始计时！" onClick="timedCount()">
    <input type="text" id="txt">
    <input type="button" value="停止计时！" onClick="stopCount()">
    <input type="button" value="重置！" onClick="resetCount()">
</form>
<p>点击上面的“开始计时”按钮来启动计时器。输入框会一直进行计时，从 0 开始。点击“停止计时”按钮可以终止计时，点击重置可终止计时,并将时间重置为0.</p>
</body>
</html>
```

运行代码：

![结果](http://img.blog.csdn.net/20151120195853828)

**说明：简单的计时器，有重置，可以停止。**

### 5. 附上时钟的代码

脚本：
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <!--<style>
        #securityCode{
            background-color: #008000;
            width:70px;
            height:30px;
            font-family: '楷体', serif;
            font-size: 20px;
            color:white;
        }
    </style>-->
    <script language="JavaScript" type="text/javascript">
     function startTime()
         {
         var today=new Date()
         var h=today.getHours()
         var m=today.getMinutes()
         var s=today.getSeconds()
         // add a zero in front of numbers<10
         m=checkTime(m)
         s=checkTime(s)
         document.getElementById('txt').innerHTML=h+":"+m+":"+s
         t=setTimeout('startTime()',500)
         }

         function checkTime(i)
         {
         if (i<10)
         {i="0" + i}
         return i
         }
        onload=startTime;
            </script>
    <title>计时</title>
</head>
<body >
<div id="txt"></div>
</body>
</html>
```

运行代码：

![结果](http://img.blog.csdn.net/20151120200331321)

**说明：时钟滴答滴答在走哦。**

**Happy hacking!**
