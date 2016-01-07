#如何获取浏览器信息
**Window有navigator对象让我们得知浏览器的全部信息.我们可以利用一系列的API函数得知浏览器的信息.**
JavaScript代码如下:
```
function message(){
            txt = "<p>浏览器代码名: " + navigator.appCodeName + "</p>";
            txt+= "<p>浏览器名称: " + navigator.appName + "</p>";
            txt+= "<p>浏览器平台和版本: " + navigator.appVersion + "</p>";
            txt+= "<p>是否开启cookie: " + navigator.cookieEnabled + "</p>";
            txt+= "<p>操作系统平台: " + navigator.platform + "</p>";
            txt+= "<p>User-agent头部值: " + navigator.userAgent + "</p>";
            document.getElementById("example").innerHTML=txt;
            if ((navigator.appName=="Netscape" || navigator.appName=="Microsoft Internet Explorer") && (parseFloat(navigator.appVersion)>=4)){
                alert("您的浏览器够先进了！");
            } else {
                alert("是时候升级您的浏览器了！");
            }
        }
 ```
#各大浏览器的基本信息
***我们可以通过这个函数通知用户浏览器是否应该去更新浏览器,同样也可以帮用户得知浏览器的相关信息***
**楼主测试了几乎当前主流的浏览器,当然不管多少浏览器都是Trident,Blink,Gecko,Webkit这几种的浏览器内核,解析上不会有太大的出入,现附上相关截图如下:**
**这是Edge的**
![这是Edge的][1]
**IE11,楼主没有用IE6,不过应该不会有太大的出入**
![IE11,楼主没有用IE6,不过应该不会有太大的出入][2]
**Safari的,楼主是Window系统Safari版本比较低**
![Safari][3]
**搜狗浏览器,曾经楼主也迷恋过它一段时间呢!**
![搜狗][4]
**QQ浏览器(微信版),比较给力,现在楼主除了Chrome用的最多的浏览器,双核Trident和Blink,Chrome内核下飞快**
![QQ浏览器(微信版)][5]
**360安全浏览器的兼容模式,也就是IE的Trident内核**
![360安全浏览器(兼容模式)][6]
**Firefox,不多说了,Netscape正版,开发者必备的浏览器**
![Firefox][7]
**Chrome.现在楼主用的最多的浏览器,Google实在是好,力挺**
![Chrome][8]
**360安全浏览器极速模式,Chrome内核,速度很快**
![360安全浏览器(极速模式)][9]
#代码结果分析
![代码介绍][10]
**Happy hacking!**
------------------------


  [1]: /img/bVq1Ng
  [2]: /img/bVq1No
  [3]: /img/bVq1NB
  [4]: /img/bVq1NE
  [5]: /img/bVq1NJ
  [6]: /img/bVq1NQ
  [7]: /img/bVq1NK
  [8]: /img/bVq1NV
  [9]: /img/bVq1NW
  [10]: /img/bVq1NZ
