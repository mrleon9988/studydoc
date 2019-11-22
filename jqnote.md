# jQuery 概述

jQuery 就是把原生的javascript的各种方法以库的形式封装起来,进行调用的一个库.



常见的javascript 库

- jQuery
- Prototype
- YUI
- Dojo
- Ext JS
- 移动端的zepto

这些库都是对原生javascript 的封装,内部都是javascript 实现的.



> jQuery 封装了 javascript 常用的功能代码:优化了DOM操作,事件处理,动画设计和Ajax交互.
>
> 学习jQuery 本质:就是学习调用这些函数(方法);
>
> jQuery 出现的目的是加快前端人员的开发速度,我们可以非常方便的调用和使用它,提高效率.



# jQuery 的基本使用

页面引入:

```
<script src="js/jquery-3.2.1.min.js" type="text/javascript" charset="utf-8"></script>
```



## 入口函数





方法一:

```
$(function () {
	...//此处是页面DOM加载完成的入口 
})
```



方法二:

```
$(document).ready(function(){
	...//此处是页面 DOM 加载完成的入口 
})
```

- 等着DOM结构渲染完成即可执行内部代码,不必等到所有外部资源加载完成,jQery 帮我们完成了封装.
- 相当于原生 js 中的DOMContentLoaded
- 不同于原生 js 中的load 事件是等页面文档\外部js文件 css文件 等资源 加载才执行内部 代码
- **所以更推荐第一种方式**



```
<div></div>
<script type="text/javascript">
	$(function () {
		$('div').hide();
	})
</script>
```



## jQuery 对象 和 DOM 对象

| 对象        | 获取方式        | 使用说明                     |
| ----------- | --------------- | ---------------------------- |
| DOM 对象    | 原生js 方式获取 | 只能使用原生js的属性和方法   |
| jQuery 对象 | jQuery 方式获取 | 只能使用 jQuery 的属性和方法 |

```
//原生方式
var div = document.querySelector('div');
	
//jquery方式
$('div')
```



**注意:jquery 对象是伪数组类型对象** 



jquery  对象 与 DOM 对象 是可以相互转换的,有的情况下,当我们要使用原生的一些属性和方法,但jquery 不提供的情况下,就需要转换了.

DOM 对象转换为 jquery 对象

```
$('div')
```

jquery 对象转换为 DOM 对象

```
$('div')[index]	//index是下标
```

```
$('div').get[index]	//index是下标
```



```
<div>
	<video src="demo.mp4" muted></video>
</div>
<script type="text/javascript">
	//比如:当jquery不提供视频自动播放时,就需要转换成dom对象提供的play方法
	//原生方式
	var div = document.querySelector('div');
	
	//jquery方式
	$('div')
	
	//转换后,视频就可以自动播放了
	$(div)[0].play();
</script>
```



## jQuery 常用的 API



### jquery 基础选择器

```
$('element') //里面的选择器直接写 语法与css一致,但要加引号
```



| 名称       | 用法            | 描述               |
| ---------- | --------------- | ------------------ |
| ID选择器   | $('#id')        | 获取ID元素         |
| 全选 择器  | $('*')          | 获取所有匹配元素   |
| 类选择器   | $('.class')     | 获取class元素      |
| 标签选择器 | $('div')        | 获取标签元素       |
| 并集选择器 | $('div,p,li')   | 获取多个标签元素   |
| 交集选择器 | $('li.current') | 获取元素里的类元素 |

jquery 层级选择器

| 名称       | 用法        | 描述                              |
| ---------- | ----------- | --------------------------------- |
| 子代选择器 | $('ul>li'); | 使用 > 号,获取当前层级下的子元素  |
| 后代选择器 | $('ul li')  | 使用空格,获取后代里的所有相同元素 |



jquery 筛选选择器

| 语法       | 用法          | 描述                     |
| ---------- | ------------- | ------------------------ |
| :first     | $('li:first') | 选择第一个li元素         |
| :last      | $('li:last')  | 选择最后一个li元素       |
| :eq(index) | $('li:eq(2)') | 选择索引号为2的li元素    |
| :odd       | $('li:odd')   | 选择索引号为奇数的li元素 |
| :even      | $('even')     | 选择索引号为偶数的li元素 |

```
<div>
	<ul>
		<li>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Totam quo.</li>
		<li>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Totam quo.</li>
		<li>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Totam quo.</li>
	</ul>
</div>
<script type="text/javascript">
	$(function () {
		$('ul li').css('color','red');	//选择ul下的li,改变样式操作
	})
</script>

```



### jquerys 筛选方法(重点)

| 语法               | 用法                           | 说明                                           |
| ------------------ | ------------------------------ | ---------------------------------------------- |
| parent()           | $('li').parent();              | 查找父级                                       |
| children(selector) | $('ul').children('li')         | 相当于$('ul>li'),查找当前下一级                |
| find(selector)     | $('ul').find('li');            | 相当于$('ul li'),后代选择器,也可以指定某个后代 |
| siblings(selector) | $('.first').siblings('li');    | 查找兄弟节点,不包括自身                        |
| nextAll([expr])    | $('.first').nextAll();         | 查找当前元素之后所有的同辈元素                 |
| prevtAll([expr])   | $('.last').prevtAll()          | 查找当前元素之前,所有的同辈元素                |
| hasClass(class)    | $('div').hasClass('protected') | 检查当前元素是否含有某个类名,如果有,返回true.  |
| eq(index)          | $('li').eq(2);                 | 相当于$('li:eq(2)'),选择第几个元素             |



#### 练习:鼠标经过显示菜单

```
     <ul class="nav">
        <li>
            <a href="#">微博</a>
            <ul>
                <li>
                    <a href="">私信</a>
                </li>
                <li>
                    <a href="">评论</a>
                </li>
                <li>
                    <a href="">@我</a>
                </li>
            </ul>
        </li>
    <script>
		$(function () {
			$('.nav>li').mouseover(function () {
				$(this).children('ul').show();
			});
			$('.nav>li').mouseout(function () {
				$(this).children('ul').hide();
			})
		})
    </script>
```





### jquery 里面的排他思想



```
<body>
	<button>按钮</button>
	<button>按钮</button>
	<button>按钮</button>
	<button>按钮</button>
	<button>按钮</button>
	<button>按钮</button>
	<script type="text/javascript">
		$(function () {
			$('button').click(function () {
				$(this).css('background','hotpink');
				$(this).siblings('button').css('background','');
			})
		})
	</script>
</body>
```



练习:鼠标经过显示对应图片

```
		<div class="container">
			<ul class="left">
				<li><a href="">图1</a></li>
				<li><a href="">图2</a></li>
				<li><a href="">图3</a></li>
				<li><a href="">图4</a></li>
				<li><a href="">图5</a></li>
			</ul>
			<div class="content">
				<div><a href=""><img src="img/hd_img1_on.jpg" alt=""></a></div>
				<div><a href=""><img src="img/hd_img2_on.jpg" alt=""></a></div>
				<div><a href=""><img src="img/hd_img3_on.jpg" alt=""></a></div>
				<div><a href=""><img src="img/hd_img4_on.jpg" alt=""></a></div>
				<div><a href=""><img src="img/hd_img5_on.jpg" alt=""></a></div>
			</div>
		</div>
		<script type="text/javascript">
			$(function () {
				// 1.鼠标经过左边的li
				$('.left li').mouseover(function () {
				// 2.得到当前li的索引号 index()
				var index = $(this).index();
				//3.右侧的图片对应左侧的索引号
				$('.content div').eq(index).show();
				//4.让其它的兄弟隐藏 siblings()
				$('.content div').eq(index).siblings().hide();
				})
				
			})
		</script>
```



### jquery 的链式编程写法

```
一般写法
$('.content div').eq(index).show();
$('.content div').eq(index).siblings().hide();

链式写法
$('.content div').eq(index).show().siblings().hide();
```

链式编程的写法,更简洁,要注意到底是**哪个对象在执行过程**



案例说明

```
<body>
	Lorem ipsum dolor sit amet, consectetur adipisicing elit. Provident beatae.
	<button>按钮</button>
	<button>按钮</button>
	<button>按钮</button>
	<button>按钮</button>
	<button>按钮</button>
	<button>按钮</button>
	
	<script type="text/javascript">
		$(function () {
			$("button").click(function () {
				// $(this).css('color','red');
				//让当前的元素变色
				// $(this).siblings().css('color','');
				//让兄弟元素颜色为空
				
				// ------------下面是链式编辑思路
				// $(this).css('color','red').siblings().css('color','');
				//1.我的颜色为红色,我的兄弟颜色为空
				// $(this).siblings().css('color','red');
				//2.我的兄弟颜色为红色,我不做任何改变,只能执行1次,没有切换效果
				$(this).siblings().parent().css('color','blue');
				//3.我的兄弟的,父级的,颜色变为蓝色,这里的父级是body
			})
		})
	</script>
</body>
```





### jquery 的样式操作

jquery 可以使用css方法来操作元素样式 ,也可以操作类,修改多个样式.



#### 一.赋值方法

1.参数只写属性名,返回的是属性值

```
$(this).css('color');	//只写了属性名,没有值,那就会返回原来的值
```

2.参数是属性名  属性值   逗号分隔  ,是设置一组样式,属性必须加引号,值是数字可以不加,不跟单位 

```
$(this).css('color','red');
```

3.参数可以是对象形式,方便设置多个样式.属性名和属性值用冒号隔开,属性可以不用加引号

```
$(this).css({
	color:red,
	"font-size":"20px",
	width:200
})
```



#### 二.设置类样式方法

作用等同于添加一个class的样式.注意操作类里面的参数**不要加点**

1.添加类

```
$('div').addClass('current');
```

2.移除类

```
$('div').remove('current');
```

3.切换类

```
$('div').toggleClass('current');
```



```
	<div class="current"></div>
	
	<script type="text/javascript">
		$(function () {
			$("div").click(function () {
				$(this).addClass('current');
				$(this).removeClass('current');
				$(this).toggleClass('current');
			})
		})
	</script>
```





#### 类操作与className 区别

| 操作方式        | 使用                               |
| --------------- | ---------------------------------- |
| 原生 javascript | 原生的会覆盖原有的类名             |
| jquery          | 只针对指定的类名操作，不影响原有的 |





#### jQuery 效果

> [jquery API 查询网站]( http://jquery.cuishifeng.cn/ /) 

jQuery 封装了很多动画效果，常见的如下：

| 显示隐藏 | 滑动          | 淡入淡出     | 自定义动画 |
| -------- | ------------- | ------------ | ---------- |
| show()   | slideDown()   | fadeIn()     | animate()  |
| hide()   | slideUp()     | fadeOut()    |            |
| toggle() | slideToggle() | fadeToggle() |            |
|          |               | fadeTo()     |            |



##### 显示隐藏效果

语法规范

```
show([speed,[easing],[fn]])
//
speed:三种预定速度之一的字符串("slow","normal", or "fast")或表示动画时长的毫秒数值(如：1000)

fn:在动画完成时执行的函数，每个元素执行一次。

[speed],[easing],[fn]Number/String,String,FunctionV1.4.3
speed:三种预定速度之一的字符串("slow","normal", or "fast")或表示动画时长的毫秒数值(如：1000)

easing:(Optional) 用来指定切换效果，默认是"swing"，可用参数"linear"

fn:在动画完成时执行的函数，每个元素执行一次。
```



##### 谈入谈出效果

> ## fadeTo([[speed],opacity,[easing],[fn]])
>
> **speed**:三种预定速度之一的字符串("slow","normal", or "fast")或表示动画时长的毫秒数值(如：1000)
>
> **opacity**:一个0至1之间表示透明度的数字。
>
> **fn**:在动画完成时执行的函数，每个元素执行一次。

speed   

opacity

**这两个参数必须写。**





##### 自定义动画

> ## animate(params,[speed],[easing],[fn])
>
> **params**:一组包含作为动画属性和终值的样式属性和及其值的集合
>
> **speed**:三种预定速度之一的字符串("slow","normal", or "fast")或表示动画时长的毫秒数值(如：1000)
>
> **easing**:要使用的擦除效果的名称(需要插件支持).默认jQuery提供"linear" 和 "swing".
>
> **fn**:在动画完成时执行的函数，每个元素执行一次。

params:想要更改的样式 属性，以对象形式传递，**必须写**

属性名可以不用带引号。





### jQuery 的属性操作

#### 1.设置或获取元素固有属性值 prop()

> 固有属性就是元素本身自带的属性:,比如 <a> 里面就有个href 



获取属性值

> prop ("属性名")

```
$(function(){
	 var a = $('a').prop('href');
	console.log(a);
})
```

设置属性值

> prop("属性名","属性值")

```
$('a').prop('title','这是设置的值');
```



#### 2.设置或添加自定义属性

> Attr('属性名')

获取属性值

```
<div data-index=1>
$('div').attr('index');	//获取index值
```

设置属性值

```
$('div').attr('index',2);	//后面跟一个数字就是设置值
```



#### 3.数据缓存

> data()方法可以在指定的元素上存取数据,并不会修改DOM元素结构,只是存在了这个**元素的内存空间里**,一旦页面刷新,数据都将被移除.

```
<span>123</span>
$('span').data('uname','mrleon');	//这里设置了一个数据
console.lgo($('span').data('uname'));	//打印出的是'mrleon'值
```



#### 练习:复选框全选

```
		<script type="text/javascript">
			$(function() {
				//1.获得全选复选框,把全选 状态赋值给其它的按钮
				$('.checkall').change(function() {
					$('.s_checkbox,.checkall').prop('checked', $(this).prop('checked'));
				})
				$('.s_checkbox').change(function() {
					if ($('.s_checkbox:checked').length === $('.s_checkbox').length) {
						$('.checkall').prop('checked', true);
					} else {
						// 不选中全选按钮
						$('.checkall').prop('checked', false);
					}
				})
			})
		</script>
```



### jQuery 内容文本值操作

> 获取\设置元素内容 html()



> 获取\设置元素文本内容 text()



> 获取\设置表单值 val()

获取方式 :括号里为空 ()

设置方式:括号里添入参数 ('123')



#### 练习:增减商品数量分析

思路:

首先声明一个变量,当我们点击 + 号 (increment),就让这个值 ++ 然后赋值给文本框 

只能增加本商品的数量,就是当前+号的兄弟文本框 (itxt) 的值

修改表单的值是 val() 方法

这个变量初始值应该是这个文本框的值,在这个值的基础上++,要先获取表单的值

当值为 1 时,就不能再继续执行递减

```
$(function() {
	$('.increment').click(function() {
		var n = $(this).siblings('.itxt').val();
		n++;
		$('.itxt').val(n);
	})
	$('.decrement').click(function() {
		var n = $(this).siblings('.itxt').val();
		if (n == 1) {
			return false;
		}
		n--;
		$(this).siblings('.itxt').val(n);
	})
})

```



#### 练习:修改商品小计的数量

思路:

每次点击 + 号 - 号,根据文本框的值 乘以 当前商品的价格 就是 商品的小计

注意1:只能增加本商品的小计,就是当前商品的小计模块 (p-sum)

修改普通元素的内容是text () 方法

注意2:当前商品的价格,要把 ￥ 符号去掉,再乘 截取字符串用 **substr (1) 方法**

 

```
$(function() {
	$('.increment').click(function() {
		var n = $(this).siblings('.itxt').val();
		n++;
		$('.itxt').val(n);
		var p = $(this).parent().siblings('.p-price').html().substr(1);
		// p = p.substr(1);
		// console.log(p);
		//计算小计的总数
		$(this).parent().siblings('.p-sum').html('￥' + p * n);
	})
	$('.decrement').click(function() {
		var n = $(this).siblings('.itxt').val();
		if (n == 1) {
			return false;
		}
		n--;
		$(this).siblings('.itxt').val(n);
		var p = $(this).parent().siblings('.p-price').html().substr(1);
		$(this).parent().siblings('.p-sum').html('￥' + p * n);
	})
	//.修改文本框的值,也要乘以商品的数量
				$('.itxt').change(function () {
					var n = $(this).val();
					var p = $(this).parent().siblings('.p-price').html().substr(1);
					$(this).parent().siblings('.p-sum').html('￥' + (p * n).toFixed(2));
				})
})

```

> parents ('选择器')  可以返回指定的或所有的祖先级元素



**保留两小位数的方法:通过  to Fixed (2) 方法设置**





### jQuery 的元素操作

> 主要是遍历、创建、添加、删除元素操作



#### 遍历元素



##### 语法1：

```
$('div').each(function (设置索引号,设置元素对象名) {执行语句})
```

**index 索引号是每个元素的索引号，元素对象是 DOM 对象 ，需要转换为 jquery 对象 $(domele)**方法

```
$(function() {
	// $("div").css("color", "red");
	// 如果针对于同一类元素做不同操作，需要用到遍历元素（类似for，但是比for强大）
	var sum = 0;
	// 1. each() 方法遍历元素 
	var arr = ["red", "green", "blue"];
	$("div").each(function(i, domEle) {
		// 回调函数第一个参数一定是索引号  可以自己指定索引号号名称
		// console.log(index);
		// console.log(i);
		// 回调函数第二个参数一定是 dom元素对象 也是自己命名
		// console.log(domEle);
		// domEle.css("color"); dom对象没有css方法
		$(domEle).css("color", arr[i]);
		sum += parseInt($(domEle).text());
	})
	console.log(sum);

```





##### 语法2

> $.each(object,function(index,element) { 执行语句;})
>
> 1. $.each () 方法可用于遍历任何对象。主要用于数据处理，比如数组、对象 
> 2. 里面的函数有2个参数：index 是每个元素的索引号; element 遍历内容

```
	// 2. $.each() 方法遍历元素 主要用于遍历数据，处理数据
	// $.each($("div"), function(i, ele) {
	//     console.log(i);
	//     console.log(ele);

	// });
	// $.each(arr, function(i, ele) {
	//     console.log(i);
	//     console.log(ele);


	// })
	$.each({
		name: "andy",
		age: 18
	}, function(i, ele) {
		console.log(i); // 输出的是 name age 属性名
		console.log(ele); // 输出的是 andy  18 属性值
	})
})
```



#### 创建元素

语法

```
$('<li></li>');	//动态创建了一个li 标签
```



##### 1.内部添加

```
elements.append('内容');
```

把内容添加目标的后面，类似原生的appendchild

**生成后，与目标是 父 、子级**

```
var li = '<li>我是添加在后面的li</li>';
var li2 = '<li>我是添加在前面的li</li>';
$('ul').append(li);
$('ul').prepend(li2);
```





##### 2.外部添加

```
element.after('内容')	//把内容添加到后面
```

```
element.befor('内容')	//把内容添加到前面
```

**生成后，与目标是 同级**



#### 删除元素

```
$('element').remove();	//可以删除匹配的目标元素
```

```
$('element').empty()	//可以删除匹配元素里面的所有子节点、元素
```

```
$('element').html("");	//括号里要加引号，代表赋值为空，作用和上一个相同 
```

