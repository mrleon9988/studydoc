# 运算符



### 比较运算符

| 符号 | 作用 | 用法                                     |
| ---- | ---- | ---------------------------------------- |
| =    | 赋值 | 把右边的值赋给左边                       |
| ==   | 判断 | 判断两边的值是否相等(此时有隐式转换效果) |
| ===  | 全等 | 判断两边的值，数据类型是否完全相同       |

```
console.log(5=='5'); //此时为true;
console.log(5==='5');此时为false;
```

```
var num1 = 10; 
var num2 = 100;
var res1 = num1 >num2; //fasle
var res2 = num1 == 11;	//false
var res3 = num1 != num2;	//true
```



### 逻辑运算符

| 逻辑       | 用法                                            |
| ---------- | ----------------------------------------------- |
| 逻辑与&&   | 判断多个条件,and，当所有的条件真时，结果为真    |
| 逻辑或\|\| | 判断多个条件,or，只要有一个条件为真时，结果为真 |
| 逻辑非 !   | 判断一个条件，not ，不是当前条件时，为真，反之  |

```
var num = 7;
var str = "我爱你~中国~";
console.log(num > 5 %% str.length >= num); //true
console.log(num <5 && str.length >= num);	//false
console.log(!(num < 10));	//false
console.log(!(num < 10 || str.length == num));	//false
```

#### 逻辑与&&

**短路运算(逻辑中断)的原理**：当有多个表达式(值)时，左边的表达式值可以确定结果时，就不再继续运算右边的表达式

- 语法:*<u>表达式1 && 表达式2*</u>

- 如果第一个表达式值为真，则返回表达式2

- 如果第一个表达式值为假，则返回表达式1

  ```
  console.log(123 && 456)；	//456	123是真，所以返回456
  console.log(0 && 456);			//0	0是假，所以返回0
  console.log(0 && 1+2 && 456*456789);	//0	0是假，所以返回0
  ```

  

#### 逻辑或||

**短路运算(逻辑中断)的原理**：如果表达式1 结果为真，则返回的是表达式1，如果表达式1 结果为假，则返回表达式2

- 语法:*<u>表达式1 || 表达式2*</u>

- 如果第一个表达式值为真，则返回表达式1

- 如果第一个表达式值为假，则返回表达式2,多个条件时，以此类推往后算

  ```
  console.log(123 || 456);	//返回 123
  console.log(0 || 456);		//返回 456
  console.log( 123 || 456 || 789 ); 	//返回123
  console.log( '' || 123 || 456);		//返回123
  
  例：
  var num = 0;
  console.log( 123 || num++);
  console.log(num);	
  //此时的Num值是多少呢，因为已经出现了逻辑中断，Num的运算并没有执行，所以返回123 num的值是0；
  ```

  

#### 赋值运算符

| 赋值运算符 | 说明                 | 例                            |
| ---------- | -------------------- | ----------------------------- |
| =          | 直接赋值             | var userName = val；          |
| +=,-=      | 加、减一个数后在赋值 | var age = 10; age += 5; //15  |
| *=，/=，%= | 乘、除、取模后在赋值 | var age = 2; age *=5;    //10 |

#### 运算符优先级

| 优先级 | 运算符     | 顺序            |
| ------ | ---------- | --------------- |
| 1      | 小括号     | ()              |
| 2      | 一元运算符 | ++ -- !         |
| 3      | 算数运算符 | 先 * / % 后 + - |
| 4      | 关系运算符 | > >= < <=       |
| 5      | 相等运算符 | == != === !==   |
| 6      | 逻辑运算符 | 先 && 后 \|\|   |
| 7      | 赋值运算符 | =               |
| 8      | 逗号运算符 | ,               |

```
console.log( 4 >= 6 || '人' != '阿凡达' && !(12 * 2 == 144) && true);	//false
先分成三块，[4 >= 6] ['人' != '阿凡达']  [!(12 * 2 == 144)] [true]
			false	||    true			true				true
var num = 10 ;
console.log( 5 == num / 2 && ( 2 + 2 * num).toString() === '22');	//true
[5 == num / 2 ] [( 2 + 2 * num).toString() === '22')]
true				true
```



### 流程控制

![](C:\Users\mrleon\Desktop\笔记\02.png)

#### 顺序流程控制

程序按照：代码的先后顺序，依次执行

#### 分支流程控制 if 语句

- 分支结构

  由上到下执行代码的过程中，根据**不同的条件**，**执行不同的路径代码**(执行代码多选一的过程)，从而得到不同的结果.

```
 条件
 判断
A	B

if (条件表达式){
//执行语句
}...
2.执行思路 如果if里面的条件表达式结果为真true，则执行大括号里面的语句
```

#### 三元运算符

1.有三元运算符组成的式子，称为三元表达式

2. ++num 3 + 5  ? :

3. 语法结构 

   //条件表达式 	？ 表达式1 ：表达式2

   4.执行思路

   //如果条件表达式结果为真 则 返回	表达式1 的值，如果条件表达式结果为假	则返回	表达式2	的值

```
var num = prompt('输入') ;
var result = num < 5 ? '0' + num : num;
结果赋到变量   条件表达    执行语句1   执行语句2
console.log(result);
```

#### switch语句

switch 语句是多分支语句，它用于基于不同的条件，执行不同的代码语句。当要针对变量设置一系列的特定值的选项时，就可以使用switch。

```
switch (value/var) {
	case value1:
	// 表达式 等于 value1时要执行的语句；
	break; //执行结束后需要打断当前语句
	case value2:
	// 表达式 等于 value2时要执行的语句；
	break;
	default:
	// 表达式 没有匹配到任何选项时要执行的语句；
}
```

1.开发时，表达式经常写成变量，

2.switch(表达式)里的值与变量的值，是一个全等的关系，===

3.如果当前的执行语句里没有break;时，就会继续向下找执行的语句，或者一直循环下去。



#### switch语句与if else if语句的区别

![](C:\Users\mrleon\Desktop\笔记\03.png)





# 循环



## for 循环解释

```
for (初始化变量；条件表达式；操作表达式（递增或递减）){
	//循环体语句
}
```

1.for循环可以重复相同的代码

2.for 循环可以重复不相同的代码

主要因为使用了计数器，计数器在每次循环过程中都会有变化

3.for 循环可以重复某些相同的操作

​	数字累加，sum = sum + i

4.for 输出结果，重复的数据可以追加字符串



## 双重for循环

循环嵌套是指在一个循环语句中再定义一个循环语句的语法结构，例如在for循环语句中，再嵌套一个for.

<img src="C:\Users\mrleon\Desktop\笔记\04.png" style="zoom: 33%;" />

```
for (外层的初始化变量；外层的条件表达式；外层的操作表达式){
	for (里层的初始化变量；里层的条件表达式；里层的操作表达式){
	//执行语句；
	}
}
```

执行过程：

1.我们可以把里面的循环看做是外层的循环语句；

2.外层循环一次，里面的循环执行全部

```
for (var i = 1; i<=3; i++){
	console.log('这是外层的第'+i+'次循环');
	for (var j = 1 ; j <= 3 ; j++){
		console.log ('这是里层的第'+j+'次循环');
	}
}
```

```
var str = '';
		for (var i = 1; i <=5 ;i++) {
			for (var j = 1; j <=5 ;j++) {
				str = str + '※';
			}
			str = str + '\n';//换行符,'\n'
		}
		console.log(str);
```

从上到下依次递减的星星

| 代码                                                         | 效果                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| var str = '';<br/>for (var i = 1; i <= 10 ; i++) { //外层循环出行数 i<br/>	for (var j = i; j <= 10; j++) {<br> //里层的列，[ i + 1]时[ j - 1 ] [ j <= 10 ] <br/>		str = str + '※';<br/>	}<br/>	str = str + '\n';<br/>}<br/>console.log(str); | ※※※※※※※※※※<br/>※※※※※※※※※<br/>※※※※※※※※<br/>※※※※※※※<br/>※※※※※※<br/>※※※※※<br/>※※※※<br/>※※※<br/>※※<br/>※ |

从上到下依次递增的星星

| 代码                                                         | 效果                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| var str = '';<br/>for (var i = 1; i <= 10 ; i++) { //外层循环行数<br/>	for (var j = 1; j <= i; j++) { <br> //里层的列[ j = 1 ]，当[ i + 1 ]时[ j + 1 ]，循环递增<br/>		str = str + '※';<br/>	}<br/>	str = str + '\n';<br/>}<br/>console.log(str); | ※<br/>※※<br/>※※※<br/>※※※※<br/>※※※※※<br/>※※※※※※<br/>※※※※※※※<br/>※※※※※※※※<br/>※※※※※※※※※<br/>※※※※※※※※※※ |



九九乘表法

| 代码                                                         |
| ------------------------------------------------------------ |
| 1x1=1	<br/>1x2=2	2x2=4	<br/>1x3=3	2x3=6	3x3=9	<br/>1x4=4	2x4=8	3x4=12	4x4=16	<br/>1x5=5	2x5=10	3x5=15	4x5=20	5x5=25	<br/>1x6=6	2x6=12	3x6=18	4x6=24	5x6=30	6x6=36	<br/>1x7=7	2x7=14	3x7=21	4x7=28	5x7=35	6x7=42	7x7=49	<br/>1x8=8	2x8=16	3x8=24	4x8=32	5x8=40	6x8=48	7x8=56	8x8=64	<br/>1x9=9	2x9=18	3x9=27	4x9=36	5x9=45	6x9=54	7x9=63	8x9=72	9x9=81 |

```
var str = '';
for ( var i = 1; i <= 9; i++) { //定义行数,循环结果9行
	for (var j = 1; j <= i ; j++) { //i+1时,j+1 j<=i
		// 公式表: 1 x 1 = 1;
		// str = str + '公式';
		// 空格转义符 \t;
		str += j + 'x' + i + '=' + i * j + '\t';
	}
	str += '\n';
}
console.log(str);
```



## while循环解释

```
var i = 1; //初始化变量
while ( i <= 10 ){ //( i <= 100 )条件表达式；
	console.log('hello.word~')//循环体
	i++;	//操作表达式;
}
```

1.while循环语法结构 ：while  当...的时候

2.执行过程：当条件表达式为true时，则执行循环体，否则退出执行

3.循环里也有计数器：初始化变量，如：var i = 1;

4.循环里也有操作表达式，完成计数器的更新，防止死循环；i++;



## do while循环解释

1.语法结构

```
var i = 1;	//初始化变量
do {
	//循环体;
	i++;	操作表达式
}while (//条件表达式);
```

2.执行过程：do ,先执行一次循环体，再执行条件表达式，结果为true时，再次从do 开始循环；否则退出循环；

3.do while循环体至少执行一次；

4.例：

```
var i = 1;
do {
	console.log ('hello.word');
	i++;
} while (i <= 10);
```

```
do {
	var msg = prompt('好吗');
} while (msg !== '好的')
console.log('回答正确');
```



## continue break

> continue 关键字：退出本次（当前次的循环），继续执行剩余的循环次数

```
for (var i = 1; i <= 100; i++){
	if ( i == 3){
		continue;//只要当条件满足if判断，就退出本次循环，直接跳到i++继续执行
	}
	console.log('输出信息');
}
```

例

```
var num = 0 ;	//初始化变量;
for (var i = 1; i <= 100; i++){	//1~100之间的数;
	if (i % 7 == 0){ //判断1~100之间，能被7整除的数外，
		continue;
	}
	num += i;		//其它数累加和；
}
console.log(num);	//输出累加结果；
```



## break

> break 关键字：退出整 个循环体，不再执行剩余次数

```
for (var i = 1; i <= 5;i++){	//循环5次
	if(i == 3){		//判断如果遇到3时
		break;		//退出整个循环，不再输出信息
	}
	console.log('执行次数' + i);//在遇到3前正常输出信息;
}
```



## 循环小结

- JS中循环有for、while、do while
- 三个循环中很多情况下都可以相互替代使用
- 如果是用来计次数，跟数字相关的、三者使用基本相同，但是我们更喜欢用for
- while和do...while可以做更复杂的判断条件，比for循环更灵活一些
- while和do...while执行顺序不一样，while先判断后执行，do...while先执行一次，再判断执行
- while和do...while执行次数不一样，do...while至少会先执行一次循环，而while可能一次也不执行
- 实际工作中，更常用for循环语句，重点学习.





# JavaScript 命名规范与语法格式



### 标识符命名规范



- 变量、函数的命名必须要有意义
- 变量的名称一般用名词
- 函数的名称一般用动词

> 变量： var = sum ; sum 是名词
>
> 函数：GetName () : 是动词





### 操作符规范

> 操作符的左右两侧保留一个空格

```
for (var i = 1; i <= 5; i++){
	if (i == 3) {
		break;
	}
	console.log('输出' + i);
}
```



### 单行注释规范

> /*
>
> */ 多行注释;
>
> //	单行注释

```
// var i = 1;单行注释
/* for (var i = 1; i <= 5; i++) {
	if (i == 3) {
		break;
	}
	console.log('输出' + i);
} */
```



### 其它规范

注意代码上、下、左、右的对齐



### 练习

1. 求1~100之间所有数的总和与平均值
2. 求1~100之间所有偶数的和
3. 求100以内7的倍数的总和
4. 使用for循环打印矩形符号，要求每次只能输出一个
5. 使用for循环打印三角形的星星符号
6. 使用for循环打印99乘法表
7. 接收用户输入的用户名与密码，若用户名为“admin”,密码为'123456'，则提示用户登录 成功；否则，一直弹出输入框；
8. 求整数1~100的累值，但要求跳过所有个位为3的数（用contiune实现）





# 数组

### 数组的创建

1.通过var arry = new Arrary()；

2.通过字面量创建：var arry = [];



获取数组的元素

通过索引(下标:用来访问数组元素的序号(数组下标从0开始)；

var arr = ['name1','name2','name3','name4'];

索引号：   0				1			2				3

数组可以通过索引访问、设置、修改对应的数组元素，可以通过 `'数组名[索引]'` 的形式来获取数组中的元素。

```
//定义数组
var arrStus = [1,2,3,];
//获取数组里的元素
console.log(arrStus[1]);//输出结果为 ' 2 ';
```

#### 练习1

> 定义一个数组，里面存放星期一、星期二....直到星期日，输出'星期日'。

```
var WeekArry = ['星期一','星期二','星期三','星期四','星期五','星期六','星期日'];
console.log(WeekArry[6]);
```



### 遍历数组

> 问：数组中的每一项我们怎么取出来？
>
> 答：可以通过'数组名[索引号]'的方式一项项的取出来。
>
> 问：如何把数组里的元素全部一起取出来？
>
> 答：使用for循环’遍历‘的方法。

```
var arr = ['red','green','blue'];
for (var i = 0; i <3 ;i++){  //i 必须是从0开始，并且只能小于数组的长度，不能用<=；
	conolse.log(arr[i]);
}
```

*遍历：就是把数组的元素全部访问一次。*

使用数组的长度一次访问：arry.length；



#### 练习2

> 求数组 [2,6,1,7,4]里面的所有元素的和及平均值；

```
	var arr = [2, 6, 1, 7, 4];
	var sum = 0;
	var avg = 0;
	for (var i = 0; i < arr.length; i++) {
		sum = sum + arr[i];
	}
	avg = sum / arr.length;
	console.log(sum, avg);
```

#### 练习3

> 求数组[2,6,1,77,52,25,7]中的最大值；

使用预值比较的方法：

```
	//创建数组
	var arr = [2,6,1,77,52,25,7];
	//声明一个max变量,并预存一个值进去
	var max = arr[0];
	//循环比较
	for (var i = 1; i < arr.length; i++) {//已经知道了第1个值，所以直接从第2个值开始；
		if ( max < arr[i]) {
			max = arr[i];
		}
	}
	console.log(max);
```

#### 练习4

> 将数组['red','green','blue','pink']转换为字符串，并用任意符号分割开

```
	//创建数组:['red','green','blue','pink']
	var arr= ['red','green','blue','pink'];
	//创建字符串变量
	var str = '';
	//创建符号变量,方便更换
	var sep = '!';
	//开始循环
	for (var i = 0; i < arr.length; i++) {
		str += arr[i] + sep;
	}
	console.log(str);
```



### 数组中新增元素

##### 修改length长度

- 可以通过修改length长度新增数组元素，不过新增的元素在没有定义是undefined;

- length属性是可读写的

  ```
  var arr = ['red','green','blue'];
  arr.length = 5;
  ```

  

##### 修改索引号

- 可以通过追加索引号，新增元素
- 如果追加的索引号已经被使用，新增的元素就会变成替换元素

```
var arr = ['red','green','blue'];
arr[3] = 'pink';
```

`不要直接给数组名赋值，会被替换原来的所有数组元素`

##### 练习1

> 新增数组元素，里面存放10个整数(1~10)；

- 使用循环来追加数组
- 声明一个空数组
- 循环中的计数器i 可以作为数组元素存入
- 由于数组索引号是从0开始，因此计数器从0开始更合适,存入的数值要+1；

```
	var arr = [];
	for (var i = 0; i < 10; i++) {
		arr[i] = i + 1;
	}
	console.log(arr);
```

##### 练习2

> 将数组[2,0,6,1,77,0,52,25,7]中大于等于10的元素选出来，放入新的数组；

方法1

```shell
var arr = [2,0,6,1,77,0,52,25,7];
	var arr2 = [];
	var j = 0;
	for (var i = 0; i < arr.length; i++) {
		if (arr[i] >= 10) {
			arr2[j] = arr[i];
			j++;	//通过这个新增的变量j，遍历追加筛选结果
		}
	}
	console.log(arr2);
```



方法2

```
	var arr = [2,0,6,1,77,0,52,25,7];
	var arr2 = [];
	for (var i = 0; i < arr.length; i++) {
		if (arr[i] >= 10) {
			arr2[arr2.length] = arr[i];
		}
	}
	console.log(arr2);
```



##### 练习3-筛选操作

> 删除[2,0,6,1,77,0,52,0,25,7] 中的0去掉后，形成一个不包含0的新数组

```shell
	var arr = [2,0,6,1,77,0,52,0,25,7];
	var newArr = [];
	for (var i = 0; i < arr.length; i++) {
		if (arr[i] != 0) {
			newArr[newArr.length] = arr[i];
		}
	}
	console.log(newArr);
```



##### 练习4-翻转数组

> 将数[1,2,3,4,5,6,7]的内容反转过来存放
>
> 输出：[7,6,5,4,3,2,1]

分析思路 : 原数组倒序 -1，新数组刚好是正序 +1；

<img src="C:\Users\mrleon\Desktop\笔记\01.png" style="zoom: 50%;" />

```shell
	var arr = [1,2,3,4,5,6,7];
	var newArr = [];
	for (var i = arr.length - 1; i >= 0; i--) {
		newArr[newArr.length] = arr[i];
	}
	console.log(newArr);
```



##### 数组排序-冒泡排序

> 基于变量替换的原理，当需要把var1 与var2 相互替换时，通过一个tempvar 进行中转。

比如：

```shell
var num1 = 'red';
var num2 = 'blue';
var temp;
temp = num1;
num1 = num2;
num2 = temp;	//temp作为中转，已经把Num1赋值到了num2里。
clonsole.log(num1,num2)
```



> 冒泡排序：是一种算法，把一系列的数据按照一定的顺序行排列显示(从小到大或从大到小);
>
> 这种简单的排序算法，重复地访问过要排序的数列，***一次比较两个元素***，如果他们的顺序错误就把他们交换过来。走访数列的***工作是重复地进行，直到没有再需要交换***，即排序完成。

<img src="C:%5CUsers%5Cmrleon%5CDesktop%5C%E7%AC%94%E8%AE%B0%5Cmp.png" style="zoom: 33%;" />

```shell
var arr = [5,4,3,2,1];
//var arr = [4,2,1,3,5];
for (var i = 0;i <= arr.length - 1;i++){ //外层循环管轮数
		//计数器都从下标0开始
		for (var j = 0;j <= arr.length -1 -1;j++) {	//里面的循环管每一轮交换的次数
			//内部交换2个变量的值前一个和后面一个数组元素相比较
			if (arr[j] > arr[j +1]) {
				var temp = arr[j];	//arr[j]是外面的数，arr[j + 1]是里面的数
				arr[j] = arr[j+1];	//把里的数替换到外面的数；
				arr[j + 1] = temp;
			}
		}
}
console.log(arr);
```





# 函数

#### 学习重点

1. 能够说明为什么需要函数
2. 能够根据语法书写函数
3. 能够根据需求封装函数
4. 能够说出形参和实参的传递过程
5. 能够使用函数的返回值
6. 能够使用arguments获取函数的参数



#### 函数的基本知识

###### 函数的概念



> 就是封装一段可以重复调用的代码块。
>
> ```shell
> function name () {
> 
> }
> ```



#### 函数的使用

1.声明函数

```shell
function 函数名 (){
	//函数体
}

function fun () {
	console.log('hello.word');
}
```

1. function 声明函数的关键词***全部小写***
2. 函数是***做某件事情***，函数名一般是***动词*** 如：getname
3. 函数不调用，函数不执行；



2.调用函数

```
函数名 ();
name ();

```



###### 练习1

> 利用函数累加1~100的值;

```shell
//1.声明函数
function getSum () {
	var sum = 0;
	for (var i = 1; i <= 100; i++){
		sum += i;
	}
	console.log(sum);
}
//2.调用函数
getSum();
```



#### 函数的参数

我们可以利用函数的参数，实现函数重复不同的代码。参数分为：形参、实参。

```shell
1.function name (形参1,形参2...){ //在声里函数里的小括号里，形参（形式上的参数）
	
}
2.name(实参1,实参2...);	//在调用函数时括号里面的参数就是，实参（实际的参数)
3.形参和实参的执行过程
function name (aru) {	//形参是接收实参的载体 aru = 'var';
	console.log(aru);
}
name(var);
4.函数的参数可以有，也可以没有，个数不限
5.注意，一旦赋于了形参，就不需要再声明相同的变量

```

##### 练习2

> 1.利用函数求任意两个数的和

```shell
function getSum (num1,num2){	//形参里已经声明了两个变量
		console.log(num1 + num2);
	}
getSum(1,2);
```



> 2.利用函数求任意两个数之间的和

```shell
	function getSum (start,end) {
		var sum = 0;
		for (var i = start;i <= end; i++) {
			sum += i;
		}
		console.log(sum);
	}
	getSum(1,10);
```

小结

- **形参可以看作已经声明了的变量**
- **如果实参的个数小于形参，未接收到值的形参会变为undefind，那么输出结果是NaN：not a number**
- **如果实参的个数大于形参，多出来的参数会被忽略掉，不参与运算**
- **实际开发中尽量让形参与实参的个数相匹配**



#### 函数的返回值

> return语句

```shell
function name () {
	return 需要返回的结果;
}
函数名();
```

- 函数只是实现的某种功能，最终的结果需要返回给函数的调用者，通过return语句，传递结果 ;

- 只要函数遇到return 就把后面的结果，返回给函数的调用者，函数名() = return 后面的结果；

  

  ```
  function  fun(num1,num2) {
  	return num1 + num2;
  }
  console.log(fun(1,2));
  ```



###### 练习 1

> 利用函数求两个数的最大值

```shell
function getMax (num1,num2) {	//1.用if方法实现
	if (num1 > num2){
		return num1;
	} else {
		return num2
	}
}
console.log(getMax(1,10));

function getMax (num1,num2) {	//2.用三元运算符实现
	return num1 > num2 ? num1 : num2;
}
console.log(getMax(2,15));
```



###### 练习2

> 利用函数求数组[5,2,99,101,67,77]中的最大值

```shell
function getArrMax (arr){	// arr 相当于接收了一个数组 arr = [5,2,99,101,67,77]
	var max = 0;
	for (var i = 1; i <= arr.length; i++){
		if (arr[i] > max) {
			max = arr[i];
		}
	}
	return max;
}
//1.得到结果：getArrMax([5,2,99,101,67,77]);实参可以是任意数据形式
//2.输出结果：console.log(getArrMax([5,2,99,101,67,77]));如果每次都这样写起来很麻烦
//如果每次都这样写起来很麻烦
//var result = getArrMax([5,2,99,101,67,77]); 声明一个变量，传递输出结果这个操作；
//console.log(result);

```

###### 小结

- return 除了返回值的作用外
- return 还可以终止函数的执行过程
- return 一次只可以返回最后的一个值，
- return 如果返回多个值，可以利用数组、对象的形式实现

```
求任意两个数的加、减、乘、除运算结果
function fun(num1,num2){
	return [num1 + num2,num1 - num2,num1 * num2,num1 / num2]
}
var result = fun(2,3);
console.log(result);
```

| break continue return的区别                                  |
| ------------------------------------------------------------ |
| break:结束当前的循环体（如for,while)                         |
| continue:跳出本次循环，继续执行剩余的循环体                  |
| return:不仅可以退出循环，还能够返回return语句中的值，同还可以结束当前的函数体内的代码 |



#### arguments的使用

> 当我们不确定有多少个参数要传递的时候，可以用arguments来获取，在javsscript 中，argumets实际上它是，当前函数的一个**内置对象**，所有函数都内置了一个arguments对象，**arguments对象中存储了传递的所有实参数值**。



```shell
function fun () {	//没有定义任何形参
	console.log(agruments);		//arguments已经接收了[1,2,3,4]的数组
}
fun (1,2,3,4);
```

arguments展示形式是一个**伪数组**，因此可以进行遍历，伪数组具有以下特点：

- 具有 length 属性

- 按索引方式储存数据

- 不具有数组的push,pop等方法

  

###### 练习

> 利用arguments求任意数的最大值

```shell
	function getMax() {
		var max = arguments[0];	//直接取数组的第1个索引值为初始值
		for (var i = 1;i <= arguments.length; i++) {	//i = 1 从第2个开始比较
			if (arguments[i] > max) {
				max = arguments[i];
			}
		}
		return max;
	}
	console.log(getMax(123,52,55,5));
```



#### 函数案例

###### 练习1 翻转排序

```shell
//将数组排序翻转一次
//声明一个函数
	function reverse(arr) {
		var newarr = [];
		for (var i = arr.length -1; i >= 0; i-- ){
				//从旧数组索引最后一个依次减1，
			newarr[newarr.length] = arr[i]; 
				//从新数组索引0开始依次加1
		}
		return newarr;	//返回新数组
	}
	var arr1= reverse([1,5,8,7,9]); //通过一个变量接收结果
	console.log(arr1);	//输出结果
```



#### 函数的两种声明方式