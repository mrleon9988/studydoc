# Vue 基础学习

## 基础指令

如何定义一个基本的vue代码结构

插值表达式 和 v-text

指令：

### v-cloak ：

清除插值表达式的显示{{}}问题



### v-html ：

设置元素的innerHTML值

```
<button type="button" value="btn" v-html="btnVal"></button>	//返回一个html按钮，可以跳转
btnVal:'<a href = "https://www.baidu.com>">跳转</a>'
```



### v-text：

设置元素的文本值

```
<button type="button" value="btn" v-text="btnVal"></button>	//返回<a>的所有文本内容
btnVal:'<a href = "https://www.baidu.com>">跳转</a>'
```



### v-bind ：

属性绑定机制 缩写：' : 属性名 '

设置元素的属性值：比如 src 、title、

设置方法1：插值表达式

```
<input v-bing:title='mytitle'>

data:{
	mytitle:'这是自定义标题'
}
```

设置方法2：取值 true\false

```
<input v-bing:active="isActive?'active':''">	//三元表达式
<input v-bing:active="{active:isActive}">	//对象表达式

data:{
	isActive:true
}
```



### v-on	 ：

事件绑定机制 缩写：'@方法名',配合下面的methos使用

```
methods: {
	doone: function() {
		console.log(11);
	},
	dotwo: function() {
		console.log(22);
	},
	changword: function() {
		this.words = 'menu2'
	}
}
```



### v- show：

根据表达值的真假，切换元素的显示和隐藏



方法1：

```
<p v-show="isshow">

data:{
	isshow:true	//初始化设置显示
}
methods:{
changShow:function(){
	this.isshow = !this.isshow	//通过点击取反操作，切换初始值，实现显示与隐藏
}
}
```

方法2：

```
<p v-show="arr.length != 0">	//通过判断数组索引来显示和隐藏

data:{
	arr:[]
}
```



### v-if：

根据表达值的真假，切换元素的显示与隐藏（操作dom元素）

方法1：

```
<p v-if="isshow">

data:{
	isshow:true
}
methods:{
	this.isshow = !this.isshow
}
```

方法2：

```
<p v-show="arr.length != 0">	//通过判断数组索引来显示和隐藏

data:{
	arr:[]
}
```





> 注意：
>
> - v - if 的本质，是通过操作dom元素来切换 显示状态
> - 表达式的值为true，元素存在于dom树中，为false时，从dom树是移除
> - 频繁的切换建议使用 v - show ，反之用 v - if ，后者的内存消耗大



### v-for:

v-for 指令的作用是：根据数据生成列表结构

数组经常和v -for 结合使用



语法1： `v-for` 指令需要使用 `item in items` 形式的特殊语法，其中 `items` 是源数据数组，而 `item` 则是被迭代的数组元素的**别名**。 

```
<li v-for="item in items">
    {{ item.message }}
  </li>

```



 语法2 ： 在 `v-for` 块中，我们可以访问所有父作用域的属性。`v-for` 还支持一个可选的第二个参数，即当前项的索引。 

```
v-for="(item, index) in items"
<li v-for="(item, index) in items">
    {{ parentMessage }} - {{ index }} - {{ item.message }}
  </li>

```



 语法3： 你也可以用 `of` 替代 `in` 作为分隔符，因为它更接近 JavaScript 迭代器的语法： 

```
<div v-for="item of items"></div>

```



语法4： 你也可以用 `v-for` 来遍历一个对象的属性。 

```
<ul id="v-for-object" class="demo">
  <li v-for="value in object">
    {{ value }}
  </li>
</ul>

```



语法5： 你也可以提供第二个的参数为 property 名称 (也就是键名)： 

```
<div v-for="(value, name) in object">
  {{ name }}: {{ value }}
</div>
```



语法6： 还可以用第三个参数作为索引： 

```
<div v-for="(value, name, index) in object">
  {{ index }}. {{ name }}: {{ value }}
</div>
```



> 在遍历对象时，会按 `Object.keys()` 的结果遍历，但是**不能**保证它的结果在不同的 JavaScript 引擎下都一致。 
>



小案例：

```
<div class="app">
	<p>数组里的数据:</p>
	<ul>
		<li v-for="(item,index) in arr">{{index+1}}{{item}}</li>
	</ul>

	<p>数组里的对象</p>
	<button type="button" @click="add">添加</button>
	<button type="button" @click="remove">移除</button>
	<h5 v-for="(item,index) in arr2"><p>{{index+1}}{{item.name}}</p></h5>
</div>


<script type="text/javascript">
	var app = new Vue({
		el: '.app',
		data: {
			arr: ["北京","天津","上海","广州"],
			arr2: [
				{name: 'menu1'},
				{name: 'menu2'},
				{name: 'menu3'},
				]
		},
		methods:{
			add:function(){
				this.arr2.push({name:'menu4'});
			},
			remove:function(){
				this.arr2.shift();
			}
		}
	})
</script>

```



### v-on : 修饰符

```
<!-- 键修饰符，键别名 -->
<input @keyup.enter="onEnter">
```



### v-model :

获取和设置表单元素的值（双向数据绑定）

```
<input v-model="message" placeholder="edit me">
<p>Message is: {{ message }}</p>
```



你可以用 v-model 指令在表单 、 及 ` 元素上创建双向数据绑定。它会根据控件类型自动选取正确的方法来更新元素。尽管有些神奇，但v-model` 本质上不过是语法糖。它负责监听用户的输入事件以更新数据，并对一些极端场景进行一些特殊处理。 

v-model` 在内部为不同的输入元素使用不同的属性并抛出不同的事件：

- text 和 textarea 元素使用 value 属性和 input 事件；
- checkbox 和 radio 使用 `checked` 属性和 `change` 事件；
- select 字段将 `value` 作为 prop 并将 `change` 作为事件。



## axios + vue 学习

axios 安装方法1

cdn引入

```
<script src="https://unpkg.com/axios/dist/axios.min.js"></script>
```



基本使用方法

```
axios.get(url?key=value&key2=value2).then(function(respose){},function(err){})

axios.post(url,{key=value&key2=value2}.then(function(respose){},function(err){})
```



/* 接口：随机笑话
			请求地址：https://autumnfish.cn/api/joke/list
			请求方法：get
			请求参数：num(笑话条数，数字)
			响应内容：随机笑话 */

```
document.querySelector('.get').onclick = function() {
	axios.get('https://autumnfish.cn/api/joke/list?num=3').
	then(function(respone) {
		console.log(respone);
	},function (err) {
		console.log(err);
	})
}
```





/* 接口：随机笑话
			请求地址：https://autumnfish.cn/api/user/reg
			请求方法：post
			请求参数：{username:name}(对象{用户名}，字符串)
			响应内容：注册成功或失败 */

```
document.querySelector('.post').onclick = function () {
	axios.post('https://autumnfish.cn/api/user/reg',{username:'mrleon'}).
	then(function (respone) {
		console.log(respone);
	})
}
```





## vue -class类操作

1.数组

```
<h1 :class="['red',green]">这是一个标题</h1>
```

2.数组中使用三元表达式

```
<h1 :class="['red','green',isactive?'active':'']">这是一个标题</h1>
```

3.数组中嵌套对象

```
<h1 :class="['red','green',{active:true}]">这是一个标题</h1>
```

4.使用对象

```
<h1 :class="{red:true,green:true,active:false}">这是一个标题</h1>
```





## 基础总结：

1.MVC 与 MVVM 的区别

2.vue最基本的代码结构

3.常用指令：

v-cloak、v-test、v-html、v-bind（缩写是：）、v-on（缩写是@）、v-model、v-for、v-if、v-show

4.事件修饰符：

.stop:阻止事件冒泡

.prevent:阻止默认行为

.capture:捕获机制

.self:自身执行函数

.once:只执行一次

5.常用属性:

el:指定控制的区域

data:是个对象,指定控制的区域里,要用到的数据

methdos:是个对象,可以自定义一些方法

6.在VM实例中,如果要访问data中的数据,或者要访问methdos里的方法,必须带 this

7.在v-for 中,要注意使用key属性, 只接收 string / number 类型

8.v-model 只能应用于表单元素里的数据绑定

9.在vue 中绑定样式的两种方法:v-bing:class  v-bing:style



