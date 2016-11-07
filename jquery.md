## jQuery

 > 1. 演示 jQuery hide() 函数，隐藏当前的 HTML 元素

```
<html>
<head>
 <script src="http://code.jquery.com/jquery-latest.js"></script>//引用的jquery文件必须是开源可用的。
<script type="text/javascript">
$(document).ready(function(){  //为了防止文档在完全加载（就绪）之前运行 jQuery 代码。
  $("button").click(function(){
  $(this).hide();//thid=nutton
});
});
</script>
</head>

<body>
<button type="button">Click me</button>
</body>

</html>
```
[image]http://localhost:63342/cssdemo/JS04.html

> 2. 演示 jQuery hide() 函数，隐藏 id="test" 的元素

```
<body>
<h2>This is a heading</h2>
<p>This is a paragraph.</p>
<p id="test">This is another paragraph.</p>
<button type="button">Click me</button>
</body>

```
只需要修改上面 1 中的一句代码

```
$(#test).hide();//"This is another paragraph."消失，点击按钮之后。
```
> 3. 隐藏所有<P>元素

```
$("p").hide();//This is a paragraph.This is another paragraph.这两句消失
```
> 隐藏class="test"的元素

```
$(.test).hide();

<body>
<h1 class="test">today is  down</h1>
<p class="test">I am unhappy</p>
<button type="button">click me</button>//点击之后，class为test的元素消失
```
1. 基础语法是：$(selector).action()
1. 美元符号定义 jQuery
1. 选择符（selector）“查询”和“查找” HTML 元素
1. jQuery 的 action() 执行对元素的操作

-  $(this).hide() - 隐藏当前元素
-  $("p").hide() - 隐藏所有段落
-  $(".test").hide() - 隐藏所有 class="test" 的所有元素
-  $("#test").hide() - 隐藏所有 id="test" 的元素
-   $("[href]") -选取所有带有 href 属性的元素


1. ==$(selector).click(function)	 触发或将函数绑定到被选元素的点击事件==
1. ==$(selector).mouseover(function)	触发或将函数绑定到被选元素的鼠标悬停事件==



```
$(document).ready(function(){
  $(".ex .hide").click(function(){
    $(this).parents(".ex").hide("slow");//父元素下的所有东西都隐藏了
  });
});

<body>

<h3>中国办事处</h3>
<div class="ex">
<button class="hide" type="button">隐藏</button>
<p>联系人：张先生<br /> 
北三环中路 100 号<br />
北京</p>
</div>

<h3>美国办事处</h3>
<div class="ex">
<button class="hide" type="button">隐藏</button>
<p>联系人：David<br /> 
第五大街 200 号<br />
纽约</p>
</div>

</body>
```

```
    $(this).parents(".ex").hide("slow")//slow也可写为1000，代表慢变化以ms计算
```

> 用toggle()表示随意切换 hide()和show()
```
$("button").click(function(){
  $("p").toggle(); /* $("p").show()+$("p").hide()*/
});
```

> jquery的淡入淡出,fadeIn,fadeTo.fadeOut

```
<!DOCTYPE html>
<html>
<head>
<script src="/jquery/jquery-1.11.1.min.js"></script>
<script>
$(document).ready(function(){
  $("button").click(function(){
    $("#div1").fadeTo("slow",0.15);//透明度0-1中取值，值越小越透明
    $("#div2").fadeIn("slow");//慢慢的出现,注意div样式dispaly:none
    $("#div3").fadeOut("3000");//慢慢的消失，3000ms
    $("#div3").fadeToggle("3000");//淡入淡出
  });
});
</script>
</head>

<body>

<p>演示带有不同参数的 fadeTo() 方法。</p>
<button>点击这里，使三个矩形淡出</button>
<br><br>
<div id="div1" style="width:80px;height:80px;background-color:red;"></div>
<br>
<div id="div2" style="width:80px;height:80px;display:none;background-color:green;"></div>
<br>
<div id="div3" style="width:80px;height:80px;background-color:blue;"></div>
<div id="div4" style="width:80px;height:80px;background-color:yellow;"></div>
</body>
</html>
```

> 动画和停止
```
<!DOCTYPE html>
<html>
<head>
<script src="/jquery/jquery-1.11.1.min.js">
</script>
<script> 
$(document).ready(function(){
  $("#start").click(function(){
    $("div").animate({left:'100px'},5000);
    $("div").animate({fontSize:'3em'},5000);
  });
  
  $("#stop").click(function(){
    $("div").stop();
  });

  $("#stop2").click(function(){
    $("div").stop(true);
  });

  $("#stop3").click(function(){
    $("div").stop(true,true);
  });
  
});
</script> 
</head>
<body>

<button id="start">开始</button>
<button id="stop">停止</button>
<button id="stop2">停止所有</button>
<button id="stop3">停止但要完成</button>
<p><b>"开始"</b> 按钮会启动动画。</p>
<p><b>"停止"</b> 按钮会停止当前活动的动画，但允许已排队的动画向前执行。</p>
<p><b>"停止所有"</b> 按钮停止当前活动的动画，并清空动画队列；因此元素上的所有动画都会停止。</p>
<p><b>"停止但要完成"</b> 会立即完成当前活动的动画，然后停下来。</p> 

<div style="background:#98bf21;height:100px;width:200px;position:absolute;">HELLO</div>

</body>
</html>
```
==$(selector).animate({params},speed,callback); animate() 方法几乎可以操作所有 CSS 属性(即params)
除了色彩。==

callback函数，指当动画完成后执行callback此函数。

```
<html>
<head>
<script type="text/javascript" src="/jquery/jquery.js"></script>
<script type="text/javascript">
$(document).ready(function(){
  $("button").click(function(){
  $("p").hide(1000,function(){
    alert("The paragraph is now hidden");//先执行hide，再执行alert
    });
  });
});
</script>
</head>
<body>
<button type="button">Hide</button>
<p>This is a paragraph with little content.</p>
</body>
</html>
```
> 同样的元素上应用多个jquery命令，名为链接（chaining）的技术
```
 $("#p1").css("color","red").slideUp(2000).slideDown(2000);
```

#### jQuery 可操作 HTML 元素和属性


```
$("#btn1").click(function(){
  alert("Text: " + $("#test").text());//弹出文本内容
});
$("#btn2").click(function(){
  alert("HTML: " + $("#test").html());//弹出文本的html
});
$("#btn1").click(function(){
  alert("Value: " + $("#test").val());//弹出文本内容
});
$("button").click(function(){
  alert($("#w3s").attr("href"));//获取属性值
});
```
