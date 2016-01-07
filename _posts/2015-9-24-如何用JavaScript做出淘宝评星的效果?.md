**楼主也是刚开始学JavaScript,觉得淘宝评星效果很棒,于是产生了自己写一个的想法**
*现附上楼主自己写的源代码*
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <script language="JavaScript" type="text/javascript">
        function star(n)
        {
            var array=new Array();
            array[0]=document.getElementById("oneStar");
            array[1]=document.getElementById("twoStar");
            array[2]=document.getElementById("threeStar");
            array[3]=document.getElementById("fourStar");
            array[4]=document.getElementById("fiveStar");
            for(var i=0;i<=n;i++)
            {
                array[i].innerText="★";
            }
            for( var j=4;j>n;j--)
            {
                array[j].innerText="☆";
            }
            document.getElementById("evaluate").innerText="您的评价是"+(n+1)+"星";
        }
    </script>
    <title>评星</title>
</head>
<body>
<strong>请您对我们作出评价:</strong>
<span id="star">
    <span style="cursor: pointer " onclick="star(0)"id="oneStar" >☆</span>
    <span style="cursor: pointer " onclick="star(1)" id="twoStar" >☆</span>
    <span style="cursor: pointer " onclick="star(2)" id="threeStar" >☆</span>
    <span style="cursor: pointer " onclick="star(3)" id="fourStar" >☆</span>
    <span style="cursor: pointer " onclick="star(4)" id="fiveStar" >☆</span>
</span><span id="evaluate"></span>

</body>
</html>
```
**楼主刚开始的时候将用了两个for循环就是这样的:**
```
 for(var i=0;i<=n;i++)
            {
                document.getElementById("fiveStar").innerText="★";
            }
            for( var j=4;j>n;j--)
            {
                document.getElementById("fiveStar").innerText="☆";
            }
```
大神们估计已经看出来了,在for循环之后HTML里的span已经失去了作用,也就是说它只能评价一次.....
**于是楼主顺着这个思路想到了用数组解决这个问题,就是让评星效果里的每一颗星储存到数组里,写出了上述的代码,可楼主还犯了一个小错误,着实困恼了许久....**
```
array[0]=document.getElementById("oneStar").innerText;
```
楼主这样定义的数组....结果可想而知,后面的代码根本无法改变评星,后来楼主想明白了,这样的定义直接将ID为onestar的元素的内容赋值给了数组,也就是说数组成了一个指向数组的指针....自然无法改变对应元素的值.
**后来楼主就算是顿悟了....**
之后又加了一些CSS效果
**成品是这样的:**
```
<!DOCTYPE html>
<head>
    <meta http-equiv="Content-Type" content="text/html; charset=gb2312" />
    <title>淘宝评分效果</title>
    <style type="text/css">
        ul, li {margin: 0; padding: 0; border: 0;}
        .shop-rating {
            height: 25px;
            overflow: hidden;
            zoom: 1;
            padding: 2px 0;
            position: relative;
            z-index: 999;
            font:12px Arial;
            color:#000;
            line-height:1.2em
        }
        .shop-rating span {
            height: 23px;
            display: block;
            line-height: 23px;
            float: left;
        }
        .shop-rating span.title {
            width: 125px;
            text-align: right;
            margin-right: 5px;
        }
        .shop-rating ul {
            float: left;
        }
        .shop-rating .result {
            margin-left: 20px;
            padding-top: 2px;
        }
        .shop-rating .result span {
            color: #ff6d02;
        }
        .rating-level,
        .rating-level a {
            background: url(http://files.jb51.net/demoimg/201007/o_star.png) no-repeat scroll 1000px 1000px;
        }
        .rating-level {
            background-position: 0px 0px;
            width: 120px;
            height: 23px;
            position: relative;
            z-index: 1000;
        }
        .shop-rating .result em {
            color: #f60;
            font-family: arial;
            font-weight: bold;
        }
        .rating-level li {
            display: inline;
        }
        .rating-level a {
            line-height: 23px;
            height: 23px;
            position: absolute;
            top: 0px;
            left: 0px;
            text-indent: -999em;
            *zoom: 1;
            outline: none;
        }
        .rating-level a.one-star {
            width: 20%;
            z-index: 6;
        }
        .rating-level a.two-stars {
            width: 40%;
            z-index: 5;
        }
        .rating-level a.three-stars {
            width: 60%;
            z-index: 4;
        }
        .rating-level a.four-stars {
            width: 80%;
            z-index: 3;
        }
        .rating-level a.five-stars {
            width: 100%;
            z-index: 2;
        }
        .rating-level .current-rating, .rating-level a:hover {background-position:0 -28px}
        .rating-level a.one-star:hover,.rating-level a.two-stars:hover,.rating-level a.one-star.current-rating,.rating-level a.two-stars.current-rating{background-position:0 -116px;}
        .rating-level .three-stars .current-rating,.rating-level .four-stars .current-rating,.rating-level .five-stars .current-rating{background-position:0 -28px;}
    </style>
</head>
<body>
<div class="shop-rating">
    <span class="title">你对我人品的评价:</span>
    <ul class="rating-level" id="stars2">
        <li><a href="javascript:void(0);" class="one-star" star:value="20">20</a></li>
        <li><a href="javascript:void(0);" class="two-stars" star:value="40">40</a></li>
        <li><a href="javascript:void(0);" class="three-stars" star:value="60">60</a></li>
        <li><a href="javascript:void(0);" class="four-stars" star:value="80">80</a></li>
        <li><a href="javascript:void(0);" class="five-stars" star:value="100">100</a></li>
    </ul>
    <span id="stars2-tips" class="result"></span>
    <input type="hidden" id="stars2-input" name="b" value="" size="2" />
</div>
<script>
    var TB = function() {
        var T$ = function(id) { return document.getElementById(id) }
        var T$$ = function(r, t) { return (r || document).getElementsByTagName(t) }
        var Stars = function(cid, rid, hid, config) {
            var lis = T$$(T$(cid), 'li'), curA;
            for (var i = 0, len = lis.length; i < len; i++) {
                lis[i]._val = i;
                lis[i].onclick = function() {
                    T$(rid).innerHTML = '<em>' + (T$(hid).value = T$$(this, 'a')[0].getAttribute('star:value')) + '分</em> - ' + config.info[this._val];
                    curA = T$$(T$(cid), 'a')[T$(hid).value / config.step - 1];
                };
                lis[i].onmouseout = function() {
                    curA && (curA.className += config.curcss);
                }
                lis[i].onmouseover = function() {
                    curA && (curA.className = curA.className.replace(config.curcss, ''));
                }
            }
        };
        return {Stars: Stars}
    }().Stars('stars2', 'stars2-tips', 'stars2-input', {
        'info' : ['人品极差', '人品不咋地', '人品一般吧', '人品不错', '人品极好啊'],
        'curcss': ' current-rating',
        'step': 20
    });
</script>
</body>
</html>
```
**Happy hacking!**
