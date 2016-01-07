**发表过一片博客《跟着我用JavaScript写计时器》,比较基础.....有网友说应该写一下setTimeout的原理和机制，嗯，今天就来写一下吧：**
###直奔主题：setTimeout和setInterval是如何工作的呢？ 
我们知道，js是单线程执行的(单线程j就是说在程序执行时，所走的程序路径按照连续顺序排下来，前面的必须处理好，后面的才会执行)。所以其实setTimeout和setInterval所谓的“异步调用”事实上是通过将代码段插入到代码的执行队列中实现的。 
而如何计算插入的时间点呢？自然是要用到我们所说的timer，也就是计时器。当执行setTimeout和setInterval的时候，timer会根据你设定的时间“准确”地找到代码的插入点。当队列“正常”地执行到插入点时，就触发timer callback，也就是我们设定的回调函数：
```
 
function fn() { 
/* 
here is some codes 
*/ alert("javascript");
setTimeout(function() {alert('ok!')},1000); 
} 
onload=fn;
```
上面这个例子就是我们通常的用法，应该容易理解。可是，timer真的能那么准确么？代码队列的执行真的能那么正常么？ 
###还记得吗？重新认识所谓的“异步” 
刚刚已经知道，事实上setTimeout和setInterval只是简简单单地通过插入代码到代码队列来实现代码的延迟执行（或者说异步执行）。但是事实上所谓的异步只是一个假象——它同样运行在一个线程上！ 始终是单线程！
那么问题就来了，要是在代码插入点前的代码执行时间超过了传入setTimeout或setInterval的设定时间会怎样呢？让我们来看看这段代码： 
```
 
function fn() { 
setTimeout(function(){alert('can you see me?');},1000); 
while(true) {} 
} 
```
你觉得这段代码的执行结果是什么呢？答案是，alert永远不会出现。 
![单线程](http://img.blog.csdn.net/20151123191143598)
这是为什么呢？因为，while这段代码没有执行完（如图，浏览器一直在解析while的代码），所以插入在后面的代码便永远不会执行。 
综上所述，其实JS终归是单线程产物。无论如何“异步”都不可能突破单线程这个障碍。所以许多的“异步调用”（包括Ajax）事实上也只是“伪异步”而已。只要理解了这么一个概念，也许理解setTimeout和setInterval也就不难了。
