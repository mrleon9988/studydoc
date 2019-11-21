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