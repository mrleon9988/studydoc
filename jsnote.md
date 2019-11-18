

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

5.循环体的最后，需要加入break 退出整个循环



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



###### 练习2 冒泡排序

```shell
function sort (arr){
	for (var i = 0;i < arr.length; i ++){	//外层循环轮数，从数组的0开始
		for(var j = 0; j < arr.length - 1 - 1; j++){	//里层循环次数
			var temp = arr[j];	//先把里面的值传到中转变量
			arr[j] = arr[j + 1];
			arr[j + 1] = temp;
		}
	}
	return arr;
}
var arr1 = sort([1,5,6,8,9,]);
console.log(arr1);
```



###### 练习3 判断闰年

> 利用函数判断闰年

```shell
num / 400 ==0

function runyear(year){
	//如果是闰年我们返回true,否则 返回false
	var flag = false;
	if (year % 4 == 0 && year % 100 !=0 || year % 400 == 0 ){
		flag = true;
	}
	return flag;
}
console.log(runyear(2010));
console.log(runyear(2012));
```



###### 函数相互调用

函数是可以相互调用的，执行顺序是第一个被调用的函数里的执行语句，**从上到下，依次执行。**

```
function fn1(){
	console.log(111);
	fn2();	//此处调用了fn2()函数;
	console.log('fn1');
}

function fn2(){
	console.log(222);
	console.log('fn2');
}
fn1();

//执行顺序：
1.从上到下，直到遇到fn1()开始执行；
2.打印 '111'
3.调用fn2(),并执行完fn2()里的所有执行语句;
4.打印 '222'
5.打印 'fn2'
6.接着执行fn1()里的执行语句；
7.打印 'fn1'
```

案例解析

```shell
//用户输入年份，判断当前年的2月份的天数
function backday(){
	var year = prompt('请输入年份');	//声明变量为被调用函数的实参 year
	//调用已经写好的判断函数
	if (runyear(year)) {
		alert('当前年是闰年，2月份有29天');
	} else {
		alert('当前年是平年，2月份有2天');
	}
}
backday();

//判断函数
function runyear(year){
	var flag = false;
	if (year % 4 == 0 && year %100 != 0 || year %400 == 0) {
		flag = true;
	}
	return flag;
}

```



#### 函数的两种声明方式

1. 利用函数关键字自定义函数 (命名函数)

```shell
function fn(){	//这里的'fn'，是我们主动命名的函数名
	//代码块；
}
fn();
```



2.函数表达式（匿名函数）

```shell
var 变量名 = function () {};
var fun = function (形参){
	console.log('这是函数表达式');
	console.log('实参');
}
fun('实参');//这里调用函数的名称，可以看到是上面声明的变量名称
```

###### 小结

1. fun是变量名，不是函数名
2. 函数表达式声明方式和声明变量差不多，一个是存值，一个是存函数
3. 函数表达式也可以进行传递参数





#### 立即执行函数


第1种写法
> ()()
> (function () {} )();(function () {} )()

第2种写法
> (function fnname(){} ());
> 

不需要调用 ,立即执行.如果有多个,要用 '; '分开

```
(function (){

console.log('1');

})()//第2个小括号,可以看作是调用函数

//这里的a,b是形参
(function (a,b) {
	console.log('111');
})(1,2)//这里的1,2是实参
```
立即执行函数里的变量,全都是**局部变量**






# JS的作用域



### 作用域

- javascript 作用域：就是代码名称（变量）在某个范围内起作用的效果，目的是为了提高**程序的可靠性，减少命名冲突**.

- js的作用域(es6)之前：全局作用域 、局部作用域

  

**全局作用域：**整个script 标签 或者是一个单独的js文件

```shell
var num = 10;
console.log(num);
```



局部作用域（函数作用域）：**在函数内部的，这个代码的名字只在函数内部工作

```
function fn(){
	//局部作用域
	var num = 20;
	console.log(num);	
}
fn();
```

输出效果：

10

20



### 变量的作用域

在javascript 中，根据作用域的不同，变量也是可以分为两种：

- 全局变量：在全局作用下的变量

```
var num = 10;
```

- 局部变量：在局部作用域（函数内部）的变量

```shell
function fun (){
	var num = 10;
	num1 = 20;	//注意
}
```



**注意：**

1. 在函数里地接赋值的 num1 = 20 变量，会被识别成全局变量
2. 全局变量只有在浏览器关闭时才会结束，比较占内存资源
3. 局部变量只有当程序执行完毕后才会结束，比较节约资源
4. 函数的形参，实际上也是局部变量





### 作用域链

> js中没有块级作用域，在es6版本中，新增了块级作用域

*什么是块级作用域：就是在 { } 里声明的变量，比如：if {} for {}*

**作用域链：内部函数访问外部函数的变量，采取的是链式查找决定取个值，就近原则！**

```
var num = 10;

function fun1(){	//外部函数
	var num = 20;
	function fun2(){	//内部函数
		console.log(num);
	}
	fun2();
}
fun1();
```

小技巧：以目标为出发，一层一层往外找，以就近原则。





# JS 的预解析



### 预解析

1. JS引擎运行JS 分为两步：**预解析 	代码执行**

- JS预解析：会把js里面所有的 var 、funciton 提升到当前作用域的最前面
- 代码执行：按照代码书写的顺序，从上往下执行











# javascript 对象

### 目标

- w才能是对象
- 创建对象的三种方式
- new 关键字
- 遍历对象属性





### 什么是对象

在javascript中，对象是组无序的相关**属性**和**方法**的集合，所有的事物都是对象，例如：字符串，数值、数组、函数等。

对象是由属性和方法组成的。

- 属性：事物的特征，在对象中用属性来表示 （常用名词）
- 方法：事物的行为，在对象中用方法来表示（常动词）





### 创建对象的三种方式

##### 1.利用字面量创建对象

对象字面量：就是花括号 { } 里面包含了表达这个具体事物（对象）的属性和方法.

```
var obj = {} ;//创建了个空对象
var obj = {
	uname: '李小花',//用逗号隔开
	age:'18',
	sex:'男',
	sayhi:function () {
		console.log('hi~');
	}
}
//1。里面的属性或者方法，采取键、值对的形式，键名：值
//2。多个属性或者方法用逗号隔开
//3。方法冒号后面跟的是一个匿名函数
//4。调用对象的属性，采取：对象名，属性名
console.log(obj.uname);
//5.调用属性的另一种方法：对象名['属性名']
console.log(obj['age']);
//6.调用对象里的函数：对象名.函数名 + （）小括号
obj.sayhi();
```



基本使用规范

| 代码格式                   | 使用说明        |
| -------------------------- | --------------- |
| console.log(start.name)    | 调用名字属性    |
| console.log(start['name']) | 调用名字属性    |
| start.sayhi();             | 调用sayhi方法， |

练习：

```
var obj = {
	name:'可可',
	type:'阿拉斯加犬',
	age:'5',
	color:'棕红色',
	skill:['汪汪汪~','演电影']
}
```



|      |      |
| ---- | ---- |
|      |      |
|      |      |
|      |      |
|      |      |

##### 2. 利用 new object 创建对象

```shell
var obj = new Object();	//创建一个空对象
//用= 号赋值,';'分号结束语句
obj.name = '李小花';
obj.age = '18';
obj.sex = '男';
obj.sayhi = function (){
	console.log('hi~');
}
```



###### 小结

1. 利用 等号 = 赋值的方法，添加对象的属性和方法
2. 每个属性和方法之间用分号结束

变量、属性、函数、方法的区别

| 标签 | 区别                                                     |
| ---- | -------------------------------------------------------- |
| 变量 | 单独声明的值，使用的时候直接写变量名，**单独存的**       |
| 属性 | **在对象里**的不需要声明，使用的时候必须是 对象.属性     |
| 函数 | 函数是单独声明，并调用的：函数名（），且是**单独存在**的 |
| 方法 | **在对象里**面，调用的时候，对象名.方法名()              |



练习

```shell
var obj = new Object;
obj.name = '鸣人';
obj.age = '18';
obj.sex = '男';
obj.skill = function (){
	console.log('影分身术');
}
console.log(obj.name);
obj.skill();
```



##### 3.利用构造函数创建对象

构造函数：是一种特殊的对象，主要用来初始化对象，即为对象成员变量赋初始值 ，它总与new运算符一起使用。我们可以把对象中一些公共的属性和方法抽取出来，然后封闭到这个函数里面。

语法规范

```shell
//声明一个构造函数
function 构造函数名 (){
	this.属性 = 值；
	this.方法 = function () {}
}

//调用构造函数
new 构造函数名();
```

```shell
	function Star (name,age,sex){ //这里定义形参
		this.name = name;	//构造函数里，这里要用分号隔开
		this.age = age;
		this.sex = sex;
		this.sing = function (song){ //定义形参：song
			console.log(song);//传实参
		}
	}
	//用构造函数创建一个对象
	var ldh = new Star('刘德华',18,'男');
	var zxy = new Star('张学友',19,'女');
	
	//输出对象
	console.log(ldh.name);
	console.log(zxy.age);
	
	//调用对象里的方法
	ldh.sing('忘情水');//赋值实参
```

练习

```shell
	function Hero (name,blood,type,attack){
		this.name = name;
		this.blood = blood;
		this.type = type;
		this.attack = function (tack){
			console.log(tack);
		};
	}
	var lp = new Hero ('廉颇',500,'力量型');
	var hb = new Hero ('寒冰',100,'射手');
	console.log(hb.name+hb.blood+hb.type);
	hb.attack('远程');
	lp.attack('近战');
```

###### 小结

1. 构造函数名字首字母要大写
2. 构造函数里不需要return 就可以返回结果 
3. 调用构造函数 必须使用 new
4. 只要new 构造函数名() 调用函数就创建了一个对象
5. 属性和方法前面必须添加 this.





### new 关键字



new 在执行时会做四件事情：

1. 在内存中创建一个新的空对象
2. 让this指向这个新的对象
3. 执行构造函数里面的代码，给这个新对象添加属性和方法
4. 返回这个新对象（所以构造函数里面不需要return



### 遍历对象属性

> 在js里遍历对象，一般采用 for ... in 



##### for ... in 语法

```shell
for (变量 in 对象名) {
}

如:
var obj = {
	name:mrleon,
	age:18,
	sex:boy
}

for (k in obj){
	console.log(k);		//k 是定义的一个变量名 ,输出结果：属性名
	console.log(obj[k]);	// obj[k] 输出结果：属性值
}
```

for ...in 里面的变量，一般用 k 或者 key



### 章节作业

1. 创建一个电脑对象，该对象要有颜色、重量、品牌、型号，可以看电影、听音乐、打游戏和敲代码

2. 创建一个按钮对象，该对象中需要包含宽、高、背景颜色和点击行为

3. 创建一个车的对象，该对象要有重量、颜色、牌子、可以载人、拉货和耕田

4. 写一个函数，实现反转任意数组

5. 写一个函数，实现对数字数组的排序

6. 项目练习：做一个简易计算器：

   1.弹窗口显示信息

   2.输入1.加法运算、2.减法运算、3.乘法运算、4.除法运算 、5.退出,6请输入您的选项





# javascrip 内置对象

### 目标

1. 能够说出什么是内置对象
2. 能够根据文档查询指定API的使用方法
3. 能够使用 Math 对象的常用方法
4. 能够使用 Date 对象的常用方法
5. 能够使用 Array 对象的常用方法
6. 能够使用 String 对象的常用方法



### 什么是内置对象



- Javascrip 中的对象分为3种：自定义对象，内置对象、浏览器对象
- 前面两种对象是 JS 基础内容，属于ECMSCRIPT:第三个**浏览器对象属于 JS 独有的**，也是 JS API。
- **内置对象**：就是指 JS 语言自带的一些对象，这些对象供开发者使用，并提供了一些常用的，或是最基本而必要的功能（功能和方法）
- 内置对象最大的优点：就是帮助我们快速开发
- JAVASCRIPT 提供了多个内置对象：Math, Date，Array，String等



### 如何查询对象文档



查询文档，可以通过 MDN / W3C 进行查询 

Mozilla 开发者网络 MDN 提供了有关开放网络技术 Open web 的信息，包括HTML\CSS\万维网，及HTML5应用的API.

MDN: https://developer.mozilla.org/zh-cn





#### Math 对象

> Math.()



##### 案例练习

```shell
function getrandomnum(max,min) {
	  return Math.floor(Math.random() * (max - min + 1)) + min; //这里是包含了1，10的写法
}

//定义一个变量接收随机值，并执行随机函数,传入参数为：1~10之间的值
var randomnum = getrandomnum(1,10);

//开始定义循环逻辑，这里使用while循环实现，只有条件满足时才退出整个程序
while (true) { // 这里的写法是，只有当为 true时，才会执行循环体
	//在这里声明一个变量，用于接收用户输入的值 ；
	var num = prompt('请输入1~10之间任意数，比大小');
	if ( num > randomnum ){
		alert('猜大了');
	} else if (num < randomnum) {
		alert('猜小了');
	} else {
		alert('恭喜你，猜对了');
		break; //这里要跳转循环
	}
}
```


```shell
	//首先，写好随机值生成的函数
	function getrandomnum(max,min) {
		  return Math.floor(Math.random() * (max - min + 1)) + min; //这里是包含了1，10的写法
	}
	
	//定义一个变量接收随机值，并执行随机函数,传入参数为：1~10之间的值
	var randomnum = getrandomnum(1,10);
	
	//开始定义循环逻辑，这里使用while循环实现，只有条件满足时才退出整个程序
	
	//声明一个次数变量
	var i = 1;
	
	while ( i <= 3 ) { // 这里的写法是，只有当为 true时，才会执行循环体
		//在这里声明一个变量，用于接收用户输入的值 ；
		var num = prompt('请输入1~10之间任意数，比大小');
		var numtime = i;
		if ( num > randomnum ){
			alert('猜大了');
		} else if (num < randomnum) {
			alert('猜小了');
		} else {
			alert('恭喜你，猜对了');
			break;
		}
		
		if (i == 3) {
			alert('3次了');
		}
		i++;
	}
```



#### Date() 日期对象

> Date() 日期对象 ，是一个**构造函数**，必须使用 new 来调用创建日期对象



```
var arr = new Array();	//创建一个数组对象
var obj = new Date();	//创建一个对象实例
```

```shell
//调用date();
var date = new Date();
console.log(date);
```

Date()方法的使用

获取当前时间必须实例化

```
var now = new Date();
console.log(now);
```

Date()构造函数的参数

如果括号里面有时间，就返回参数里面的时间。例如日期格式为字符串'2019-01-01',可以写成new Date('2019-01-01'),或者 new Date('2019/01/01')



##### 日期格式化

```shell
var date = new Date();
console.log(date.getFullyear());	//返回当前日期的年份
console.log(date.getMonth() + 1);	//默认返回的月份要比当前小1个月，记得要+1
console.log(date.getDate);	//返回当天是几号
console.log(date.getDay);	//默认返回的是周1-周6，0代表周日

//如果写成中文格式
var year = date.getFullyear();
var month = date.getMonth() + 1;
var day = date.getDate();
var week = date.getDay();

	var date = new Date();
	console.log(date.getFullYear());	//返回当前日期的年份
	console.log(date.getMonth() + 1);	//默认返回的月份要比当前小1个月，记得要+1
	console.log(date.getDate());	//返回当天是几号
	console.log(date.getDay());	//默认返回的是周1-周6，0代表周日
	
	//如果写成中文格式
	var year = date.getFullYear();
	var month = date.getMonth() + 1;	//记得要+1
	var dates = date.getDate();
	
	//定义星期的中文数组
	var weekarr = ['星期日','星期一','星期二','星期三','星期四','星期五','星期六']	//默认获取数据是从 0 ,1-6，
	var week = date.getDay();	//因为没有中文日期的星期转换，只有手动关联对应的星期
	
	console.log('今天是：'+ year + '年' + month + '月' + dates + '周' + weekarr[week]);
	
	
	//得到时分秒
		function gettime() {
		var time = new Date();
		var h = time.getHours();
		h = h < 10 ? '0' + h : h;	//利用三元运算，加个'0'在时间的前面
		var m = time.getMinutes();
		m = m < 10 ? '0' + m : m;
		var s = time.getSeconds();
		s = s < 10 ? '0' + s : s;
		
		return h + ':' + m + ':' + s;
	}
	
	console.log(gettime());
```



获取Date 总的毫秒数（时间戳），不是当前时间的毫秒数，是距离1970年1月1日起，到当前过了多少毫秒

1. 通过valueOf   getTime()

   var date = new Date();

   console.log(date.valueOf());

   console.log(date.getTime());

2. 简单的写法 （最常用的写法）

   var date1 = +new Date(); 	//+new Date() 如果不传参，返回**当前**总的毫秒数

   console.log(date1);

3. H5 新增的 

   console.log (Date.now());

##### 案例练习

倒计时

分析思路：

核心算法：用户输入的时间，减去现在的时间，就是剩余时间。

用时间戳来做，用户输入时间总的毫秒数，减去现在的时间总的毫秒数，得到的就是剩余时间总毫秒数

把剩余时间总毫秒数转换为天、时、分、秒（时间戳转换为时分秒）

转换公式如下：

d = parseInt( 总秒数 / 60 / 60 / 24)；	//计算天数

h = parseInt( 总秒数 / 60 60 % 24);	//计算小时

m = parseInt (总秒数 / 60 % 60);	//计算分钟数

s = parseInt (总秒数 % 60)；	//计算当前秒数



```shell
	function countDown(time){
		var nowTime = +new Date();	//返回当前的时间总毫秒
		var inputTime = +new Date(time);	//用户输入的时间毫秒数，也就是将来的时间
		var times = (inputTime - nowTime) / 1000;	//1秒等于1000，所以把毫秒数转换为秒
					//将来的时间 - 当前时间
		var d = parseInt(times / 60 / 60 / 24);	//得到天数
		d = d < 10 ? '0' + d : d;
		var h = parseInt(times / 60 / 60 % 24);	//得到小时
		h = h < 10 ? '0' + h : h;
		var m = parseInt(times / 60 % 60);	//得到分钟数
		m = m < 10 ? '0' + m : m;
		var s = parseInt(times % 60);	//得到当前的秒
		s = s < 10 ? '0' + s : s;
		return d + '天'+ h + '小时'+ m + '分钟'+ s +'秒';
	}
	
	console.log(countDown('2019-11-12 17:00:00'));
```





# JavaScript DOM 操作



### 如何获取DOM

```js
document.getElementById('元素选择器');
// id ('idname')
// class('.idname')
```

小结：

1.默认文档元素是从上到下开始查找，所以，一般script语法要放在元素下里

```javascript
<div>
<script>
<body>	
```

2.get 获得 element 元素 by 通过 驼峰命名法

3.参数 id 是大小写敏感的字符串

4.返回的是一个元素对象 object 对象

5.console.dir(dom) 可以打印返回的元素对象，能更好的查看里面的**属性和方法**



#### 根据标签名获取 



> 使用 getElementsByTagName() 方法可以返回带有指定标签名的对象集合



```javascript
	<ul>
			<li>content</li>
			<li>content</li>
			<li>content</li>
		</ul>
	<script type="text/javascript">
	var lis = document.getElementsByTagName('li');	//获取到所有的 li 标签的元素
	</script>
```

//1.返回的是获取过来元素对象的集合,以伪数组的形式存储的
			var lis = document.getElementsByTagName('li');
			console.log(lis);
			//如何要获取第几个元素
			console.log(lis[0]);
	

#### 根据 ID 名获取

```javascript
		<ul>
			<li>content</li>
			<li>content</li>
			<li>content</li>
		</ul>
		<ol id='ol'>
			<li>content</li>
			<li>content</li>
			<li>content</li>
		</ol>

		//2.如果要依次打印里面的元素对象,可以采取遍历的方法
		for ( var i = 0; i < lis.length; i++){
			console.log(lis[i]);
		}
		
		//3.如果页面中只有一个 li 返回的还是伪数组
		
		//4.如果页面中没有这个元素,返回的还是空的伪数组
		
		//5.如果有多个相同元素,但处理不同父元素下,获取 方法使用 document.getElementsByTagName('标签名')
		//  且父元素必须是指定的单个元素
		var ol = document.getElementsByTagName('ol');
		console.log(ol[0]);
		
		// 一般使用简单的方法获取 
		var ol = document.getElementsByTagName('ol');	 //这里的ol 是id名
		console.log(ol.getElementsByTagName('li')); 	//这里的ID 是 ol 下的 li 元素
```


#### 根据 class 类名获取

​		

```javascript
document.getElementsByClassName('类名');
//根据类名返回元素对象集合,这是HTML5新增的方法 ,要注意兼容性
```



#### querySelector () 方法获取 

```javascript
document.querySelector();
//这是HTML5新增的一种类选择器方法，返回的是**第一个**元素对象，切记：( )里加符号，class  = ' . ' 加点， id = ' # ',加井号;
```

```javascript
document.querySelector('.box');	//返回第一个class 类名的元素对象
document.querySelector('#box');	//返回第一个id 类名的元素对象
```

```javascript
document.querySelectorAll('.box');
//后面加 All 可以获取到所有相同选择器的元素对象
```



#### 获取特殊元素 body,html



- 获取body元素

```javascript
var body =  document.body;
// 这个元素是可以获取到的
```



- 获取 html元素

```javascript
var html = document.html;
// 这个元素用这个方法是获取不到的
```

```javascript
document.documentElement;
//这个方法可以获取 hmtl 元素对象；
```





### 事件基础

#### 执行事件的三要素步骤

1. 获取事件源
2. 注册事件(绑定事件)
3. 添加事件处理程序（采取函数赋值形式）



> 点击一个按钮，弹出对话框

```javascript
	<button id="btn">点击按钮</button>
	
<script type="text/javascript">
	// 点击按钮,弹出对话框
	//1.事件有三部分组成:事件源/事件类型/事件处理程序 ,也称事件三要素
	//1.1 事件源,事件被触发的对象 ,谁 ————按钮
	var btn = document.getElementById('btn');
	//1.2 事件类型 ,如何触发——什么事件——比如鼠标点击(onclick)
	//1.3 事件处理程序 通过一个函数赋值的方式 完成
	btn.onclick = function(){
		alert('我是弹框');
	}
</script>
```


> 点击元素，打印信息

```javascript
	<div>123</div>

	<script type="text/javascript">
		// 1. 获取事件源
		var div = document.querySelector('div');
		// 2. 注册事件(绑定事件)
		// 3. 添加事件处理程序（采取函数赋值形式）
		div.onclick = function() {
			console.log('我被选中了');
		}
	</script>
```


### 常见的鼠标事件

| 鼠标事件    | 触发条件     |
| ----------- | ------------ |
| onclick     | 鼠标点击     |
| onmouseover | 鼠标经过     |
| onmouseout  | 鼠标移出     |
| onfocus     | 获得鼠标焦点 |
| onblur      | 失去焦点     |
| onmousemove | 鼠标移动     |
| onmouseup   | 鼠标弹起     |
| onmousedown | 鼠标按下     |



### 操作元素

javascript 的 DOM 操作可以改变网页内容、结构 、样式、还可以改变内容的属性等。





##### 改变元素内容



```javascript
element.innerText	//修改里面的文字
```

从起始位置到终止位置的内容，但它会去除html标签，同时空格和换行也会去掉

```javascript
element.innerHTML	//w3c标准，一般推荐使用这个
```

起始位置到终止位置的全部内容，包括html标签，同时保留空格和换行



案例练习

```javascript
	<button type="button">显示系统时间</button>
	<div></div>
	<p></p>
	<script type="text/javascript">
        // 要求：点击按钮，div里显示系统当前时间
		// 1. 获取事件源
		var btn = document.querySelector('button');
		var div = document.querySelector('div');
		// 2. 注册事件(绑定事件)
		btn.onclick = function () {
			div.innerText = '2019-09-09';	//改变元素的内容
		}
		// 3. 添加事件处理程序（采取函数赋值形式）
		
		// 要求:页面加载时,就显示当前系统时间
		// 已经编辑好的获取系统时间的函数
		function getDate() {
			var date = new Date();
			var year = date.getFullYear();
			var month = date.getMonth() + 1;	//记得要+1
			var dates = date.getDate();
			
			//定义星期的中文数组
			var weekarr = ['星期日','星期一','星期二','星期三','星期四','星期五','星期六']	//默认获取数据是从 0 ,1-6，
			var week = date.getDay();	//因为没有中文日期的星期转换，只有手动关联对应的星期
			
			return '今天是：'+ year + '年' + month + '月' + dates + '周' + weekarr[week];
		}
		
		//1.获取元素
		var p = document.querySelector('p');
		//2.注册事件
		p.innerText = getDate();		//改变元素的内容
	</script>
```


##### 改变元素的属性

常见的属性操作

| 标签属性  | 说明                     |
| --------- | ------------------------ |
| innerText | 元素的文字内容           |
| innerHTML | 元素的HTML标签内容       |
| src       | 元素的路径               |
| href      | 元素的链接地址           |
| id        | 元素的id类名             |
| alt       | 图片元素的alt说明文字    |
| title     | 图片元素鼠标移入时的文字 |



```javascript
	<button type="button" id="ldh">刘德华</button>
	<button type="button" id="zxy">张学友</button>
	<img src="img/hd_img1.jpg"	alt="" title="刘德华">
	<script type="text/javascript">
		//要求:点击明星按钮,切换不同的图片
		//1.获取元素
		var ldh = document.getElementById('ldh');
		var zxy = document.getElementById('zxy');
		var img = document.querySelector('img');
		
		//2.注册事件
		ldh.onclick = function () {
			img.src = 'img/hd_img1.jpg';
			img.title = '刘德华';
		}
		zxy.onclick = function () {
			img.src = 'img/hd_img2.jpg';
			img.title = '张学友';
		}
	</script>
```


##### 案例练习

> 分时显示不同图片，显示不同问候语

- 根据不同时间，页面显示不同图片，同时显示不同的问候语
- 如果上午时间打开页面，显示上午好，显示上午的图片
- 如果下午时间打开页面，显示下午好，显示下午的图片
- 如果晚上时间打开页面，显示晚上好，显示晚上的图片

```javascript
<img src="img/morning.jpg" alt="">
<div></div>
<script type="text/javascript">
	//根据不同时间段,显示不同的图片与问候语
	//1.获取元素
	var img = document.querySelector('img');
	var div = document.querySelector('div');
	//2.注册事件
	//利用new Date()函数获取当前时间的小时数
	var date = new Date();
	var h = date.getHours();
	//3.创建一个多分支语句
	if (h < 12){
		img.src = 'img/morning.jpg';
		div.innerHTML = '早上好，好好学习';
	} else if (h < 18) {
		img.src = 'img/after.gif';
		div.innerHTML = '下午好，好好学习';
	} else if(h < 23) {
		img.src = 'img/night.gif';
		div.innerHTML = '晚上好，好好学习';
	}
</script>
```


##### 表单元素的属性操作



利用 DOM 可以操作如下表单元素的属性

| 元素     | 属性                    |
| -------- | ----------------------- |
| type     | 类型                    |
| value    | 值                      |
| checked  | 选择状态                |
| selected | 选中状态                |
| disabled | 启用状态（true / false) |

**表单里面的值，是通过 value 来改变的**

小案例

```javascript
<button type="button">按钮</button>
<input type="" name="" id="" value="还没有点我" />
<script type="text/javascript">
	//要求:点击按钮,改变 输入框 里的值
	//1.获取元素
	var input = document.querySelector('input');
	var btn = document.querySelector('button');
	//2.注册事件
	btn.onclick = function () {
		input.value = '被点击了';	//改变input 的值
		// btn.disabled = true;	//一般这样写
		this.disabled = true;	//如果只是当前表单,可以改成this
	}
</script>
```
小案例

```javascript
//点击眼睛图标，切换input的显示效果,pwd 与 text
<div class="box">
	<label>
		<img src="img/close.png" >
	</label>
	<input type="password" name="" id="" value="" />
</div>
<script type="text/javascript">
	var input = document.querySelector('input');
	var img	= document.querySelector('img');
	var label = document.querySelector('label');
	var flag = 1;
	//2.注册事件
	label.onclick = function () {
		if (flag == 1) {
			img.src = 'img/open.png';
			input.type = 'text';
			flag = 0;
		} else {
			img.src = 'img/close.png';
			input.type = 'password';
			flag = 1;
		}
	}
</script>
```





##### 样式属性操作

可以通过 JS 修改元素的大小、颜色 、位置等 css 样式

- element.style	css行内样式操作
- element.className 类名样式操作

```javascript
<div style= 'width:400px;backgroundColor:#ff0000'></div>
<script type="text/javascript">
	var div = document.querySelector('div');
	div.onclick = function () {
		this.style.backgroundColor = '#ff0000';
		this.style.width = '400px';
	}
```
注意：

1. JS 里面的样式名采取驼峰命名 比如：fontSize backgroundColor
2. JS 修改 style 样式操作，产生的是行内样式，直接在元素上添加，权重最高



小案例

```javascript
//要求：点击关闭图标，整个box隐藏,
<div class="box">
	<div class="code"></div>
	<i id="close-btn"></i>
</div>
<script type="text/javascript">
		var btn = document.querySelector('#close-btn');
		var box = document.querySelector('.box');
		btn.onclick = function () {
			box.style.display = 'none';
		}
</script>
```


小案例

```javascript
//要求：利用循环，自动依次更换li标签的背景图标
<div class="box">
	<ul>
		<li></li>
	</ul>
</div>
<script type="text/javascript">
	 var lis = document.querySelectorAll('li');
	 var spans = document.querySelectorAll('span');
	 for (var i = 0; i < lis.length; i++){
		 //new一个变量接收图标的Y坐标值
		 var index = i * 44;	//因为图标是纵向的，每个图标向下间隔44px
		 //改变元素背景图的坐标值
		lis[i].style.backgroundPosition = '0 -'+index+'px';
		
	 }
	 for (var k = 0; k < spans.length; k++){
		spans[k].innerText = '文字';
	 }
	 console.log(spans);
</script>
```
小案例

```javascript
//要求：焦点的切换状态，输入框里的文本改变内容、样式
<div class="box">
	<input value="手机" />
</div>
<script type="text/javascript">
	var text = document.querySelector('input');
	text.onfocus = function () {
		if (this.value === '手机') {
			this.value = '';
			this.style = 'color:#333';
		} 
	}
	text.onblur = function () {
			this.value = '手机';
			this.style = 'color:#999';
	}
	
</script>
```



###### 小结：

1. 如果样式修改较少，可以采取操作行内样式的方式，此方便法的 CSS 权重最高
2. 如果样式修改较多，可以采取操作类名更改的方式，此方法可直接修改 class id 类
3. class id 因为是个保留字，因此使用className 来操作元素类名属性
4. className 全直接更改元素的类名，会覆盖原来的类名
5. 如果要保留原先的class类名，添加一个新的class 类，需要在赋值 的时候加上空格

```javascript
	<div class="firstClass"></div>
	<script type="text/javascript">
		var div = document.querySelector('div');
		div.onclick = function () {
			div.className = 'addClass';
			div.className = 'firstClass addClass'
		}
	</script>
```


练习

​		//要求：判断输入框输入的数字长度,并给出相对应的提示信息

```javascript
	<div class="box">
		<input type="password" class="ipt">
		<p class="tips">请输入6~10位数的密码</p>
	</div>
	<script type="text/javascript">
		//1.数字长度要求6-10位
		//2.失去焦点的时候显示信息
		//3.准备3个提示小图标
		//1.获取元素
		var ipt = document.querySelector('.ipt');
		var tips = document.querySelector('.tips');
		ipt.onblur = function() {
			if (this.value.length < 6 || this.value.length > 10) {
				tips.className = 'tips error';
				tips.innerHTML = '输入的数字错误';
			} else {
				tips.className = 'tips right';
				tips.innerHTML = '输入正确';
			}
		}
	</script>
```


##### 作业

1. 用户名 输入框 默认提示文字显示隐藏效果

   ```javascript
   	<input type="" name="" id="ipt" value="用户名/邮箱号" />
   	<script type="text/javascript">
   		// 用户名 输入框 默认提示文字显示隐藏效果
   		var ipt = document.querySelector('input');
   		ipt.onfocus = function () {
   			this.value = '';
   			this.className = 'ipt ipts';
   		}
   		ipt.onblur = function () {
   			this.value = '用户名/邮箱号';
   			this.className = 'ipt'
   		}
   	</script>
   ```

2. 顶部通栏广告 点击关闭效果

   ```javascript
   	<div class="topAd">
   		<i class="closeBtn"></i>
   	</div>
   	<script type="text/javascript">
   		// 顶部通栏广告 点击关闭效果
   		var btn = document.querySelector('.closeBtn');
   		var adbox = document.querySelector('.topAd');
   			btn.onclick = function () {
   				adbox.style = 'display:none';
   			}
   	</script>
   ```

3. 下拉菜单 鼠标移入显示,移出隐藏效果

   ```javascript
   	<div class="navbox">
   		<a href="" class="navbar">menu</a>
   		<div class="showmenu">
   			<ul>
   				<li><a href=""></a>menu</li>
   				<li><a href=""></a>menu</li>
   				<li><a href=""></a>menu</li>
   			</ul>
   		</div>
   	</div>
   	<script type="text/javascript">
   		var m1 = document.querySelector('.navbar');
   		var m2 = document.querySelector('.showmenu');
   		m1.onmouseover = function () {
   			m2.style.display = 'block';
   		}
   		m2.onmouseout = function () {
   			this.style.display = 'none';
   		}
   	</script>
   ```

4. 开关灯 点击按钮切换背景色

   ```javascript
   	<button type="button">开/关按钮</button>
   	<script type="text/javascript">
   		// 开关灯 点击按钮切换背景色
   		var btn = document.querySelector('button');
   		var bd = document.body;
   		var flag = 0;
   		btn.onclick = function () {
   			if(flag == 0){
   				bd.style.background = '#222222';
   				flag = 1;
   			} else if(flag == 1){
   				bd.style.background = '#fff';
   				flag = 0;
   			}
   		}	
   	</script>
   ```

#### 排他思想

| 元素  |       |       |       |
| ----- | ----- | ----- | ----- |
| 按钮1 | 按钮2 | 按钮3 | 按钮4 |

如果有同一组元素,我们只想切换选中某一个元素的时候,需要用到循环的排他思想算法

步骤:

1. 选择所有元素,清除样式或状态
2. 给当前选中的元素符加样式或状态
3. **注意执行顺序不能错**,要从上向下依次执行



案例

```javascript
	<div class="box">
		<button>按钮1</button>
		<button>按钮2</button>
		<button>按钮3</button>
		<button>按钮4</button>
	</div>
	<script type="text/javascript">
		var btns = document.getElementsByTagName('button');
		for (var i = 0; i < btns.length; i++) {
			btns[i].onclick = function() {
				for (var i = 0; i < btns.length; i++) {
					btns[i].style.backgroundColor = '';
				}
			this.style.backgroundColor = 'red';
			}
		}
	</script>
```
###### 练习

```javascript
	//切换皮肤效果,点击预览图,指定的元素跟着切换图片
	<div class="box">
		<img src="img/hd_img1.jpg" alt="">
		<img src="img/hd_img2.jpg" alt="">
		<img src="img/hd_img3.jpg" alt="">
		<img src="img/hd_img4.jpg" alt="">
	</div>
	<div class="showimg"></div>
	<script type="text/javascript">
		var imgs = document.querySelector('.box').querySelectorAll('img');
		var show = document.querySelector('.showimg');
		// console.log(imgs);
		for (var i = 0;i<imgs.length;i++){
			imgs[i].onclick = function () {
				show.style.background = 'url('+this.src+')';	//指定切换下面的图
				// document.body.style.background = 'url('+this.src+')'; //指定切换body背景图
			}
		}
	</script>
```
练习

```javascript
//要求:鼠标经过/移出表格行的时候,切换背景色样式	
<script type="text/javascript">
		//1.获取 元素
		var trs = document.querySelector('tbody').querySelectorAll('tr');
		for (var i = 0; i < trs.length; i++) {
			trs[i].onmouseover = function() {
				this.className = 'bg';
			}
			trs[i].onmouseout = function () {
				this.className = '';
			}
		}
	</script>
```
另一种实现思路,可以指定  tr  的 :hover 效果



###### 练习:全选 与 反选

```javascript
//要求:当选中全选按钮时,下面其它的选择框都跟着切换选中状态,并且,其它选择框可以单独操作.	
<script type="text/javascript">
		//1.获取 元素
		var choseBtn = document.getElementById('choseAll');
		var allcd = document.querySelector('tbody').querySelectorAll('input');
		choseBtn.onclick = function () {
			for (var i = 0;i<allcd.length;i++){
				//this.checked .是当前全选按钮的选中状态,复选 框返回的是布尔型 true 或 false
				allcd[i].checked = this.checked;	//全选框选中,就把状态同样赋给其它选择框
			}
		}
	</script>

//要求2:判断其它按钮只要有一个没有选中,上面的全选按钮就不选中,满足条件就选中
for (var i = 0; i < allcd.length; i++) {
	//获取当前按钮的选中状态
	allcd[i].onclick = function() { //只要所有的小按钮都选中了,全选按钮就是选 中状态
		flag = true; //声明一个变量,控制全选按钮是否选中
		for (var i = 0; i < allcd.length; i++) {
			if (!allcd[i].checked) { //如果当前的按钮没有选中,[ 这里采用了取反的算法 ]
				flag = false; //默认肯定是小按钮都没有选中,所以全选按钮默认也是未选中
				break; //这里打断,是为了不让这个判断一直循环检测,选中1个打断一次
			}
		}
		choseBtn.checked = flag; //如果满足条件,全选 按钮就是true;
	}
}

```





###### 练习：切换 tabs 标签

```javascript
		//1.获取标签、内容区元素
		var tabs = document.querySelectorAll('.h-nav');
		var items = document.querySelectorAll('.item');
		// console.log(tabs);
		// console.log(con);
		for (var i = 0; i < tabs.length; i++) {
			tabs[i].setAttribute('index', i);
			tabs[i].onclick = function() {
				for (var i = 0; i < tabs.length; i++) {
					tabs[i].className = ''; //先清除所有的样式
				}
				this.className = 'active'; //再给当前的赋于样式

				//2.下面的内容区，跟着变化 而变化 
				var index = this.getAttribute('index');
				for (var i = 0; i < items.length; i++) {
					//先干掉所有的
					items[i].style.display = 'none';
				}
				//留下当前的
				items[index].style.display = 'block';
			}
		}
```


### 自定义属性操作

​	有的时候，可以设置一个些元素的自定义属性来操作DOM，为了只在前端页面里使用而提出的一个种方法。

| 语句                                      | 作用                                                         | 兼容性 |
| ----------------------------------------- | ------------------------------------------------------------ | ------ |
| elements.setAttribute( 'name',' value ' ) | 设置属性名、值                                               | IE.H5  |
| elements.getAttribute( ' name' )          | 获取属性的值                                                 |        |
| elements.dataset                          | 获取属性的值,包含了所有以 data-name的自定义属性              | H5新增 |
| elements.dataset['name']                  |                                                              |        |
| elements.dataset.listName                 | 如果属性名有多个，如data-list-name,那在获取的时候要把名字以驼峰命名法连起来 |        |
| elements.dataset['listName']              |                                                              |        |



```javascript
	<div class="dv" getTime="20" data-time='20' data-list-name='30'></div>
	<script type="text/javascript">
		var div = document.querySelector('.dv');
		console.log(div.getAttribute('getTime'));
		console.log(div.dataset);
		console.log(div.dataset.time);
		console.log(div.dataset.listName);
```




### 节点操作

获取元素通常使用两种方式：

| 利用DOM获取元素                 | 利用节点层级关系获取元素   |
| ------------------------------- | -------------------------- |
| document.getElementById()       | 利用父、子、兄节点关系获取 |
| document.getElementsByTagName() | 逻辑性强，但是兼容性稍差   |
| document.querySelector等        | children 、Parent          |
| 逻辑性不强、繁琐                |                            |

两种方法都可以使用，但是节点操作相对更简单些



#### parentNode

```javascript
<div class="box">
	<div class="son">btn</div>
</div>
var btn = document.querySelector('.btn')	//首先获取目标子节点
var box = btn.parentNode	//获取目标的父节点，
console.log(box)
console.log(btn.parentNode)
```

注意：节点获取只能得到离目标最近的父级节点，如果找不到返回的是 null



#### childrenNodes\children

```javascript
console.log(box.children);
可以获取子元素节点，推荐使用这个方法

console.log(box.childNodes);
可以获取子级的所有元素节点，包含元素、文本等，一般不使用这个方法
```

#### 在子级里获取第几个子节点

```javascript
element.firstChild	//获取第一个，
element.lastChild	//获取最后一个
但是得到的是文本元素
```

```javascript
element.firstElementChild
element.lastElementChild
//这样获取到的才是子元素节点

//注意：IE9以上才兼容
```

解决方法：

```javascript
element.children[0];
//通过索引号直接获取，第一个肯定是 0

如果在不确定总个数的情况下，获取最后一个
//element.children[element.children.length - 1];
```

这个方法没有兼容性问题！



##### children 练习

```javascript
//要求:鼠标移入一级菜单,显示下拉菜单,移出隐藏下拉菜单
<script>
	// 1. 获取元素
	var nav = document.querySelector('.nav');
	// 得到4个小li
	var lis = nav.children;
	// 2.循环注册事件
	for (var i = 0; i < lis.length; i++) {
		lis[i].onmousemove = function () {
			this.children[1].style.display = 'block';
		}
		lis[i].onmouseout = function () {
				this.children[1].style.display = 'none';
			}
	}
</script>
```



### 创建\添加节点

```javascript
node.createElement ('li');
```

1.创建节点元素

```javascript
var li = document.createElement('li');

2.从后面添加节点
node.appendChild(child) node 是父级, chiild 是子级,从后面追加元素,类似于数组中的push

var ul = document.querySelector('ul');

ul.appendChild(li);

3.从前面添加节点
var lis = documents.createElement('li');
ul.insertBefor(lis,ul.children[0]);
              (目标,父级的第一个子级前面)
```



基本步骤:

1. 创建元素: createElement ( ' ' );

2. 添加元素位置: 

   向后添加:appendChild(创建的元素)

   向前添加:insertBefor ( 创建的元素变量,父级的第 [ 0 ] 个位置开始 )

	
	
	```
	1. <body>
	
	   	<ul class="nav">
	   		<li>
	   			<a href="">aaa</a>
	   			<div>
	   				<p>Lorem ipsum dolor sit.</p>
	   			</div>
	   		</li>
	   	</ul>
	
	   </body>
	
	   <script type="text/javascript">
	   	//获取要添加目标的父级元素
	   	var par = document.querySelector('ul');
	   	//2.创建子级元素
	   	var sonli = document.createElement('div');
	   	//3.添加到指定位置
	   	par.appendChild(sonli);
	
	<body>
	
		<ul class="nav">
			<li>
				<a href="">aaa</a>
				<div>
					<p>Lorem ipsum dolor sit.</p>
				</div>
			</li>
		</ul>
	
	</body>
	
	<script type="text/javascript">
		//获取要添加目标的父级元素
		var par = document.querySelector('ul');
		//2.创建子级元素
		var sonli = document.createElement('div');
		//3.添加到后面的位置
		par.appendChild(sonli);
		//4.添加到前面的位置
		par.insertBefore(sonli,par.children[0]);
						//元素后面跟一个逗号
	
	
	```
	
	
	
	**注意:这样的写法一次只能添加一个,下面的不会执行**





#### 练习:简单对话框

```javascript
	<div class="container">
		<!-- 文本框 -->
		<textarea rows="" cols=""></textarea>
		<!-- 按钮 -->
		<button type="button">发布</button>
		<!-- 对话li标签 -->
		<ul>
		</ul>
	</div>

</body>
<script type="text/javascript">
	//获取元素
	var btn = document.querySelector('button');
	var text = document.querySelector('textarea');
	var ul = document.querySelector('ul');
	//注册事件
	//输入信息,点击按钮,创建li标签,把信息赋值到li标签,添加到ul里
	btn.onclick = function() {
		if (text.value == '') {
			alert('内容为空,请输入');
			return;
		} else {
			var li = document.createElement('li');
            //赋值给Li
			li.innerHTML = text.value;
			//这是从后面添加
			// ul.appendChild(li);
			//这是从前面添加
			ul.insertBefore(li, ul.children[0]);
			//提交后清空文本框内容
			text.value = '';
		}
	}
</script>
```


### 删除节点

```javascript
node.removeChild(父元素.children[第几个])
```

node.removeChild(child) 方法从 DOM 中删除一个子节点,返回删除的节点;

		<div class="container">
			<button type="button">按钮</button>
			<ul>
				<li>一</li>
				<li>二</li>
				<li>三</li>
			</ul>
		</div>
	</body>
	<script type="text/javascript">
		//获取父元素
		var ul = document.querySelector('ul');
		var btn = document.querySelector('button');
		// node.removeChild(父元素.children[第几个])
		btn.onclick = function() {
			if (ul.children.length === 0) {
				this.disable = true;
			} else {
				ul.removeChild(ul.children[0]);
			}
		}
	</script>


练习2

	<script type="text/javascript">
		//获取元素
		var btn = document.querySelector('button');
		var text = document.querySelector('textarea');
		var ul = document.querySelector('ul');
		//注册事件
		//输入信息,点击按钮,创建li标签,把信息赋值到li标签,添加到ul里
		btn.onclick = function() {
			if (text.value == '') {
				alert('内容为空,请输入');
				return;
			} else {
				var li = document.createElement('li');
				//赋值给Li
				li.innerHTML = text.value + "<a href='javascript:;'>删除</a>"; //创建一个删除按钮在后面
				//这是从后面添加
				// ul.appendChild(li);
				//这是从前面添加
				ul.insertBefore(li, ul.children[0]);
				//提交后清空文本框内容
				text.value = '';
	
				//每条留言后面增加一个删除按钮
				//删除元素,删除的是当前链接的li 该元素的父级
				var as = document.querySelectorAll('a'); //获取所有的删除a 标签
				
				for (var i = 0; i < as.length; i++) {
					as[i].onclick = function() {
						// node.removeChild(父元素.children[第几个])
						ul.removeChild(this.parentNode);
						//删除的是li 当前a所在li this.parentNode
					}
				}
			}
		}
	</script>




### 复制节点

```
node.cloneNode()
```

node.cloneNode() 方法返回调用该 方法的节点的一个副本.也称为克隆节点、拷贝节点



注意：

1.如果**括号**参数为**空或才false**，则是浅拷贝，即只克隆复制节点本身，不克隆里面子节点（内容）

2.括号里参数：true   false/空



		<div class="container">
			<ul>
				<li>1</li>
				<li>2</li>
				<li>3</li>
			</ul>
		</div>
	</body>
	<script type="text/javascript">
		//1。首先获取父元素node.cloneNode()
		var ul = document.querySelector('ul');
		//2.复制子节点元素
		//   目标           复制
		var newli = ul.children[0].cloneNode();
		//向后添加
		ul.appendChild(newli);
		//向前添加
		// ul.insertBefore(newli,ul.children[0]);
	</script>


### 动态表格的生成与操作

```javascript
<body>
		<table cellspacing="0">
			<thead>
				<tr>
					<th>姓名</th>
					<th>科目</th>
					<th>成绩</th>
					<th>操作</th>
				</tr>
			</thead>
			<tbody>

			</tbody>
		</table>
	</body>
	<script type="text/javascript">
		// 1.先准备好学生的数据,创建对象数据组 var data = [1,2,3];
		var datas = [{
			name: '张小三',
			subject: 'HTMLCSS',
			score: 100,
		}, {
			name: '李狗蛋',
			subject: 'HTMLCSS',
			score: 96,
		}, {
			name: '王二麻',
			subject: 'HTMLCSS',
			score: 90,
		}, {
			name: '周扒皮',
			subject: 'HTMLCSS',
			score: 85,
		}, {
			name: '赵小红',
			subject: 'HTMLCSS',
			score: 76,
		}];

		//2.向tbody里创建行,利用for循环读取数组的长度
		var tbody = document.querySelector('tbody');
		for (var i = 0; i < datas.length; i++) {
			//创建tr行
			var tr = document.createElement('tr');
			//插入到tbody里
			tbody.appendChild(tr);

			//行里面创建td 单元格,数量取决于每个对象里的属性个数,遍历对象用for...in方法
			// for (变量 in 对象名) {	}
			for (var k in datas[i]) {
				//1.创建单元格,
				var td = document.createElement('td');
				//2.把对象里的属性值,赋值给td
				td.innerHTML = datas[i][k]; //datas[i]的[i]是第几个属性,[k]是第几个的属性值
				tr.appendChild(td);
			}

			//创建有删除按钮的单元格
			var td = document.createElement('td');
			td.innerHTML = '<a href="javascrpit:;">删除</a>';
			tr.appendChild(td);

		}
		//按钮可以删除关联的tr行
		var as = document.querySelectorAll('a');
		for (var i = 0; i < as.length; i++) {
			as[i].onclick = function() {
				// ul.removeChild(this.parentNode);这里找的关系 是爸爸的爸爸
				tbody.removeChild(this.parentNode.parentNode);
			}
		}
	</script>
```





### 三种创建元素的区别



1.document.write()   创建元素，如果页面文档流加载完，再调用此方法，页面会被重绘

```
var btn = document.querySelector('button')

btn.onclick = function (){

document.write('<div>123</div>div>');
}
```



2.innerHTML 创建元素

innerHTML,是将内容写入某个DOM节点，不会导致页面全部重绘

innerHTML 创建多个元素效率更高（在不拼接字符串的情况下，采取数组形式拼接），但结构稍微复杂。



3.document.createElement()  创建元素

createElement() 创建多个元素效率稍低一点点，但是结构更清晰



总结：不同浏览器下，innerHTML 效率要比 createElement 高



### DOM 重点核心总结

关于DOM操作，主要有创建、增、删、改、查、属性操作、事件操作



#### 创建

1. document.write

2. innerHTML

3. createElement

   

#### 增

1. appendChild：向后添加
2. insertBefore：向前添加



#### 删

removeChild



#### 改

1. 主要修改dom的元素属性，dom元素的内容，属性、表单的值等
2. 修改元素属性：src  href  title等
3. 修改普通元素内容：innerHTML   innerText
4. 修改表单元素：value  type   disabled等
5. 修改元素样式：style   className



#### 查

1. ###### 主要获取查询 dom 的元素

2. DOM提供的API方法：getElementById  getElementsByTagName，古老用法，不太推荐

3. H5提供的新方法：querySelector   querySelectorAll 推荐使用

4. 利用节点操作：父parentNode   子children  兄previousElementSibling  nextElementSibling



#### 属性操作

主要针对自定义属性

1. setAttribute ：设置dom的新属性值
2. getAttribute：得到dom的新属性值
3. removeAttribute：移除新属性



#### 事件操作

主要给元素注册事件，采取 事件源——事件类型 = 事件处理程序 

| 鼠标事件    | 触发条件     |
| ----------- | ------------ |
| onclick     | 鼠标点击     |
| onmouseover | 鼠标经过     |
| onmouseout  | 鼠标移出     |
| onfocus     | 获得鼠标焦点 |
| onblur      | 失去焦点     |
| onmousemove | 鼠标移动     |
| onmouseup   | 鼠标弹起     |
| onmousedown | 鼠标按下     |



# JS的高级事件



### 注册事件（绑定事件）

**传统注册方式**

1. 利用on 开头的事件

2. ```
   <button onclick = "alert('hi~')"></button>button>
   ```

3. btn.onclick = function(){}

4. 特点：注册事件的唯一性

5. 同一个元素同一个事件只能设置一个处理函数，最后注册的处理函数将会覆盖前面的。



**方法监听注册方式**

1. w3c标准 推荐方法
2. addEvenlistener() 它是一个方法
3. IE9前的IE不支持，可以使用attachEvent() 代替
4. 特点：同一个元素同一个事件可以注册多个监听器
5. 按注册顺序依次执行



### addEventlistener 事件监听方式

```
evenTarget.addEventlistener(type,listener[,useCapture])
```

eventTarget.addEventlistener()方法将指定的监听器注册到eventTarget(目标对象)上，当该对象触发指定的事件时，就会执行事件处理函数。

该方法接收三个参数：

- type：事件类型字符串，比如click  mouseover  注意这里不带 on

- listener：function：可以写在里面，也可以写在外面，调用时输入函数名，不带小括号

- useCapture：可选参数，是一个布尔值 ，默认是false

  



```
<button type="button" class="innerbtn">按钮</button>
<script type="text/javascript">
			//事件监听器
				//1。获取元素
				var btn = document.querySelector('button');
				//2。注册事件
				btn.addEventListener('click',function(){
					alert('hello');
				});
</script>
```



### 删除事件（解绑事件）

1.传统解绑方法：divs[0].onclick = null; 赋值为空

2.H5新解绑方法：divs[1].removeEventListener('click',fn); 函数要写在外面，



```
<body>
		<div>1</div>
		<div>2</div>
		<div>3</div>
	</body>
	<script type="text/javascript">
		//获取 所有div元素
		var divs = document.querySelectorAll('div');
		//第1种兼容较好的老方法
		divs[0].onclick = function () {
			alert('11');
			//弹一次后就移除该函数
			divs[0].onclick = null;
		}
		
		//第2 种新的方法
		divs[1].addEventListener('click',fn)
		//事件函数要写在外面，在小括号里调用，注意在调用时不用加小括号
		function fn() {
			alert(22);
			divs[1].removeEventListener('click',fn);
		};
		
		//第3种，针对IE8以下的方法
		divs[1].attachEvent('click',fn1);
		function fn1() {
			alert(22);
			divs[1].detachEvent('click',fn1);
		};
	</script>
```



### 事件对象



> eventTarget.onclick = function(**event**)  {}
>
> eventTarget.addEventListener('click',funciton(**event**) {} )
>
> //这个event 就是事件对象，一般可以简写 **e**  或  **evt**

简单理解：事件发生后，跟事件相关的一系列信息数据的集合都放到这个对象里，这个对象就是事件对象event,它有很多属性和方法。打印event可以查看详细属性。



		<div>1</div>
	</body>
	<script type="text/javascript">
		var div = document.querySelector('div');
		div.onclick = function (evt) {
			console.log(evt);
			
			// console.log(window.event);//这是兼容ie8以下的写法
			
			//解决方案：
			evt = evt || window.event
			console.log(evt)
		}
		
		div.addEventListener('click',function (e) {
			console.log(e);
		})
	</script>



### 阻止事件冒泡的两种方式

事件冒泡：开始时最具体的元素接收，然后逐级向上传播到DOM最顶层节点。

事件冒泡本身的特征，会带来的坏处，也会带来的好处，需要灵活掌握。

1。标准写法：利用事对象里面的 stopPropagation ()  方法

```
		<div class="father">
			<div class="son"></div>
		</div>
	</body>
	<script type="text/javascript">
		//阻止冒泡，dom推荐的标准 stopPropagtion()
		var son = document.querySelector('.son');
		var father = document.querySelector('.father');
		
		son.addEventListener('click',function (e) {
			alert('son');
			e.stopPropagation();
		},true);
		
		father.addEventListener('click',function () {
			alert('father');
		});
		
	</script>
```



### 事件委托（代理、委派）

场景描述：

```
<ul>
	<li>我的一个元素</li>
	<li>我的一个元素</li>
	<li>我的一个元素</li>
	<li>我的一个元素</li>
	<li>我的一个元素</li>
</ul>
```

**点击每个  li  都会弹出对话框，以前需要给每个 li 注册事件，很麻烦，而且访问DOM的次数有5次，这就会延长页面的交互就绪时间。**

这样的情况就可以通过**事件委托**来解决：

事件委托的原理：

不是每个子节点单独设置事件监听器，而是事件监听器设置在父节点上，然后利用冒泡原理影响设置每个子节点。

场景案例：给 ul 注册点击事件，然后利用事件对象的 target 来找到当前点击的 li ,因为点击 li ，事件会冒泡到 ul 上，ul 有注册事件，就会触发事件监听器



**事件委托的作用**

我们只操作一次DOM，就可以解决子节点重复事件的性能影响。

```
		<ul>
			<li>我的一个元素</li>
			<li>我的一个元素</li>
			<li>我的一个元素</li>
			<li>我的一个元素</li>
			<li>我的一个元素</li>
		</ul>
	</body>
	<script type="text/javascript">
		//事件委托的核心原理，给父节点添加监听器，利用事件冒泡影响每一个子节点
		//1.演示效果：点击每个li 弹个对话框
		var ul = document.querySelector('ul');
		ul.addEventListener('click',function (e) {
			// alert('我是一个元素');
			//也可以改变每个li 的样式操作,
			e.target.style.backgroundColor = 'blue';
		});
	</script>
```





### 常用的鼠标事件



1.禁止鼠标右键菜单: ' contextmenu '

```
document.addEventListener('contextmenu',function (e) {
			e.preventDefault();// 这是阻止事件的规定语法
		})
```

2.禁止鼠标选中：' selectstart '

```
document.addEventListener('selectstart',function (e) {
			e.preventDefault();// 这是阻止事件的规定语法
		})
```



### 鼠标事件对象

**event** 对象代表事件的状态，跟事件相关的一系列信息的集合，现阶段我们主要是用鼠标事件对象MouseEvent  和键盘事件对象 KeyboardEvent。



| 鼠标事件对象 | 说明                                    |
| ------------ | --------------------------------------- |
| e.clientX    | 返回鼠标相对于浏览器窗口可视区的 X 坐标 |
| e.clientXY   | 返回鼠标相对于浏览器窗口可视区的 Y 坐标 |
| e.pageX      | 返回鼠标相对于文档页面的 X 坐标         |
| e.pageY      | 返回鼠标相对于文档页面的 Y 坐标         |
| e.screenX    | 返回鼠标相对于电脑屏幕的 X 坐标         |
| e.screenY    | 返回鼠标相对于电脑屏幕的 Y 坐标         |



##### 案例练习：跟随鼠标的天使

思路分析：

1. 鼠标不断移动，使用鼠标移动事件：mousemove
2. **在页面中移动，给document注册事件**
3. 图片要移动距离，而且不占位置，使用绝对定位
4. 核心原理：每次鼠标移动，获取新的鼠标坐标，把这个x y的值 做为图片的，top left 的值 就可以移动图片

```
		<style type="text/css">
			img {
				position: absolute;
			}
		</style>
	</head>
	<body>
		<img src="../img/angel.gif">
	</body>
	<script type="text/javascript">
		var pic = document.querySelector('img');
		document.addEventListener('mousemove', function(e) {
			var x = e.pageX;
			var y = e.pageY;
			pic.style.left = x + 'px';
			pic.style.top = y + 'px';
		})
	</script>
```





### 常用的键盘事件

事件除了使用鼠标触发，还可以使用键盘触发。

| 键盘事件  | 触发条件                                                     |
| --------- | ------------------------------------------------------------ |
| onkeyup   | 某个键盘按键被松开时触发                                     |
| onkeydown | 某个键盘按键被按下时触发                                     |
| onkeyress | 某个键盘按键被按下时触发（但不识别功能键 如ctrl  shift 箭头等 |

document.onkeyup = function(){}

document.addEventListener('keyup',function())



执行顺序是：keydown -> keypress -> keyup



注意：

keydown  keyup 不区分字母大小写，keypress 区分

实际开发中，更多的使用keydown  keyup 它们能识别所有键

可以通过ASCII 码值 区别判断按下的键是不是要求的。



案例练习：

按下  s  键 ，输入框获取 焦点

	<body>
		<input type="" name="" id="" value="" />
	</body>
	<script type="text/javascript">
		var search = document.querySelector('input');
		document.addEventListener('keyup',function (e) {
			if(e.keyCode === 83){
				search.focus();
			}
		})
	</script>


案例练习：

输入数字，显示更大的同步数字框

		<div class="wrap">
			<div class="con"></div>
			<input type="" name="" id="key" value="" />
		</div>
	</body>
	<script type="text/javascript">
		var con = document.querySelector('.con');
		var input = document.querySelector('input');
		input.addEventListener('keyup', function(e) {
			if (this.value == '') {
				con.style.display = 'none';
			} else {
				con.style.display = 'block';
				con.innerHTML = this.value;
			};
		})
		//如果失去焦点，变隐藏上面的提示框
		input.addEventListener('blur',function(){
			con.style.display = 'none';
		});
	</script>





# JavaScript BOM 操作

### BOM概述：

> BOM (Browser Object Model) **浏览器对象模型**，它提供了独立于内容而与**浏览器窗口进行交互**的对象，其核心对象是**window**
>
> BOM 由一系列相关的对象构成，并且每个对象都提供了很多方法与属性。
>
> BOM 缺乏标准，javascript 语法的标准化组织是ECMA，DOM 的标准化组织是W3C，BOM 最初是NETSCAPE 浏览器标准的一部分，**估兼容性比较差**。



BOM 的构成

window 包含以下以象：**document  location  navigation  screen  history**

**window 对象是浏览器的顶级对象**，它具有双重角色。

它是 js 访问浏览器窗口的一个接口

它是一个全局对象。定义在全局作用域中的变量、函数都会变成window对象的属性和方法。

一般我们在调用的时候可以省略window，比如：alert(); 完整 写法是 window.alert();

**注意：window 下的一个特殊属性 winodw.name** ，这个name 尽量不要使用.



### window 对象的常见事件

#### 1.窗口加载事件

```
传统方式
wnidow.onload = function (){}

H5方式
window.addEventListener('load',function(){});
```

window.load ：是窗口（页面）加载事件，当文档内容完全加载完成，会触发该事件（包括图片、脚 本文件、css文件）等，就调用的处理函数 。

注意：

1. 有了window.onload 就可以把js 代码写到页面元素的任意位置，或者引入js文件
2. window.onload 传统注册事件方式只能写一次，只会执行最后面的一次。
3. window.addEventListener 则没有限制 



另一种预加载 事件方法：**DOMContenLoaded**

```
document.addEventListener('DOMContenLoaded',function(){});
```

该事件触发时，只会预先 DOM 元素加载完成渲染，不包括：css 图片 flash 等等。

比如：页面里的图片很多的情况下，从用户访问到onload 触发可能 会要较长时间，此时用DOMContenLoaded 方法，就比较好，**预先把元素框架渲染完成**，再去加载其它图片元素。



#### 2.调整窗口大小事件

```
window.onresize = function(){}

window.addEventListener('resize',function(){});
```

注意：

只要窗口大小发生像素变化，就会触发这个事件

我们经常利用这个事件完成响应式布局，window.innerWidth / innerHeight 当前屏幕的宽度

```
		//当窗口发生改变，div元素隐藏或显示 
		<div class="container">
		</div>
		<script type="text/javascript">
		window.addEventListener('load',function () {
			var div = document.querySelector('div');
			window.addEventListener('resize',function () {
				if(window.innerWidth >= 800){
					div.style.display = 'block';
				} else {
					div.style.display = 'none';
				}
			})
		})
		</script>
```



#### setTimeout () 定时器

```
1.window.setTimeout (function(),延时时间毫秒值);
```



```
setTimeout(function () {
	console.log('时间到');
},2000);
```

```
// 可以先声明一个函数，然后在计时器里调用
function callback() {
	console.log('我来啦');
}
setTimeout(callback, 3000);
```

```
var timer1 = setTimeout(callback, 3000);
//第1个3秒执行
var timer2 = setTimeout(callback, 5000);
//第2个5秒执行
```



注意：

1. 这个window在调用的时候可以省略
2. 这个延时时间单位是毫秒，但是可以省略，如果省略默认的是 **0**
3. 这上调用函数可以直接写函数 ，还可以写  函数名 ，或者采取字符串'函数名()'的形式，第3种不推荐
4. 因为定时器可能 有很多，所以我们经常经定时器赋值 给一个标识符。


##### 案例练习

5秒后自动关闭广告

```
		<div class="container">
			<img src="img/morning.jpg" class="ad">
		</div>
		<script type="text/javascript">
			var ad = document.querySelector('.ad');
			setTimeout(function(){
				//执行程序直接写在计时器里
				ad.style.display = 'none';
			},5000);
```




#### 停止 setTimeout 定时器
```
window.clearTimeout (timeoutID)
```



clearTimeout()方法取消了先前通过调用 setTimeout() 建立 的定时器。



**注意：**

- window 可以省略

- 里面的参数就是定时器的标识符,就是要停止 ‘哪个定时器’ 的意思


```
		<div class="container">
			<img src="img/morning.jpg" class="ad">
			<!-- 停止按钮 -->
			<button>停止</button>
		</div>
		<script type="text/javascript">
			var ad = document.querySelector('.ad');
			var stopbtn = document.querySelector('button');
			var timer1 = setTimeout(function(){
				//执行程序直接写在计时器里
				ad.style.display = 'none';
			},5000);
			
			//停止定时器
			stopbtn.addEventListener('click',function () {
				console.log('停止了');
				clearTimeout(timer1);
			})
		</script>
```



#### setInterval () 定时器

```
window.setInterval(回调函数，[间隔的毫秒数]);
```

**setInterval() 方法重复调用一个函数，每隔这个时间，就去调用1次这个回调函数**


```
setInterval(function () {
	console.log('输出');	//每隔1秒输出1次
},1000);
```





案例练习：倒计时
```
		<div class="container">
			<span class="hour">1</span>
			<span class="min">2</span>
			<span class="sec">3</span>
		</div>
		<script type="text/javascript">
			var hour = document.querySelector('.hour');
			var min = document.querySelector('.min');
			var sec = document.querySelector('.sec');
			
			var inputTime = +new Date('2019-11-17 18:00:00'); // 返回的是用户输入时间总的毫秒数：就是预计结束的时间
			countDown();
			setInterval(countDown,1000);
			//时间获取函数 
			function countDown() {
			    var nowTime = +new Date(); // 返回的是当前时间总的毫秒数
			    var times = (inputTime - nowTime) / 1000; // times是剩余时间总的秒数 
			    var h = parseInt(times / 60 / 60 % 24); //时
			    h = h < 10 ? '0' + h : h;
			    hour.innerHTML = h; // 把剩余的小时给 小时黑色盒子
			    var m = parseInt(times / 60 % 60); // 分
			    m = m < 10 ? '0' + m : m;
			    min.innerHTML = m;
			    var s = parseInt(times % 60); // 当前的秒
			    s = s < 10 ? '0' + s : s;
			    sec.innerHTML = s;
			}
		</script>
```



#### 停止setInterval() 定时器

```
		<div class="container">
			<button type="button" class="star">开启</button>
			<button type="button" class="stop">停止</button>
		</div>
		<script type="text/javascript">
			var star = document.querySelector('.star');
			var stop = document.querySelector('.stop');
			//要先声明一个传递回调函数的变量
			var timer = null;
			
			//注册事件
			star.addEventListener('click',function () {
			timer = setInterval(function () { //这里把回调函数传到全局变量
					console.log('hello');
				},1000);
			})
			
			stop.addEventListener('click',function(){
				clearInterval(timer);//这里就可以写明停止的事件函数
			})
		</script>
```

案例练习：发送短信倒计时


```
		<div class="container">
			手机号：<input type="text" class="iptNum">
			<button type="button" class="sendBtn">发送</button>
		</div>
		<script type="text/javascript">
			var btn = document.querySelector('button');
			var time = 3;//初始化计时数字变量

			btn.addEventListener('click', function() {
				btn.disabled = true;
				var timer = setInterval(function() {
					if (time == 0) {//计时数字满足条件后
						clearInterval(timer);//停止
						btn.disabled = false;//恢复按钮
						btn.innerHTML = '发送';//改变文字
					} else {
						btn.innerHTML = '还剩下' + time + '秒'; //动态提示信息
						time--;循环递减
					}
				},1000);
			});
		</script>
```



### this 的指向问题

this 一般情况下 this 的最终指向的是那个**调用它的对象**

1.**全局作用域** 或者 普通函数中 this 指向全局对象 window(定时器里面的this 指向window)

```
console.log(this);
function fn(){
console.log(this);
}
window.fn();	//这里完整的写法,可以看出是this 是指向了window
-----------
window.setTimeout(function(){
	console.log(this);
},1000);	//这里的this 也是指向window
```


2.**方法调用中**,谁调用,this就指向谁

```
var o = {
	sayhi:function(){
		console.log(this);	//这里的this,是指向了 o,由这个变量 o 去调用的
	}
}

```

3.**构造函数** 中 this 指向构造函数的实例

```
function Fun(){
	console.log(this);	//这里的this 指向是fun 实例对象
}

var fun = new Fun();	//只要是new 的都是一个实例对象 
```





### JS的执行机制

js 为了解决单线程 执行效率的问题,利用多核cpu 的计算能力,HTML5 提出WEB WORKER 标准,允许javacript 脚本创建多个线程 .于是,JS中出现了**同步**和**异步**.

```
//这个执行顺序是什么呢,
			console.log(1);
			
			setTimeout(function () {
				console.log(3);
			},1000)
			
			console.log(2);

//结果是:1 2  3,

```

**执行机制分析**:

JS 在执行多任务的时候,会把执行 分类进入两大区域内:主要执行栈、任务队列里,

| 主线程执行栈          | 任务队列 |
| ------------------- | -------- |
| console.log (1)     | fn       |
| setTimeout (fn , 0) |          |
| console.log (2)     |          |

首先，把有回调函数的任务，分到**任务队列**里，然后开始主要执行栈，并把任务队列的结果，**放到执行栈**的最后面。



1.先执行**执行栈中的同步任务**

2.异常任务（回调函数）放入任务队列中

3.等待执行栈中的所有同步任务执行完毕，系统就会按次序 读取 **任务队列**中的异常任务，于是被读取的异常任务结束等待状态 ，进入 s执行栈，开始执行。

```
			console.log(1);
			
			setTimeout(function () {
				console.log(3);
			},0)
			
			console.log(2);
```
这个案例的执行结果是：1 2 3;


```
console.log(1);
document.onclick = function () {
	console.log('click');
}
console.log(2);
setTimeout (function () {
	console.log(3);
},3000)
```



> 如果页面中出现了多个异常任务，结果还是和执行机制一样，但如果有类似等待用户点击后再执行的任务，会进入事件循环的情况，就是每次执行完了，任务清空，再次触发 再走一遍smrmh机制。比如：可以重复用按钮执行任务的场景 。





### location 对象

> window 对象给我们提供了一个**location 属性**用于**获取或设置窗体的URL**,并且**可以用于解析URL**，因为这个属性**返回的是一个对象**，所以我们将这个属性也称为 location 对象 。
> 


location 对象的属性


| location	  | 返回值	    |
| ----------- | --------- |
| location.href	| 获取或者设置整个URL |
| location.host | 返回主机（域名)     |
| location.port | 返回端口号，如果未写返回空字符串 |
| location.pathname | 返回路径 |
| location.search | 返回参数 |
|location.hash | 返回片断 #后面内容 常见于链接 描点操作 |



练习1：5秒自动跳转网址



```
<div class="container">
	<button type="button">跳转</button>
	<div class="tips"></div>
</div>
<script type="text/javascript">
		var btn = document.querySelector('button');
		var div = document.querySelector('.tips');
		
		btn.addEventListener('click',function () {
			location.href = 'https://www.baidu.com';
		})
		//声明数字变量
		var time = 5;
		// setInterval(fn,1000);
		function fn() {
			setInterval(function () {
				if(time == 0) {
					location.href = 'https://www.123.com';
				}else{
					div.innerHTML = ''+time+'秒倒计时跳转网址';
					time--;
				}
			},1000)
		}
</script>

```



#### location 获取URL参数

> location.search 方法



1. 表单设置
2. 传递参数
3. 截取参数
4. 分割字符
5. 输出数据




```
//page1
	<body>
		<!-- // 1.第一个登录页面,里面有提交表单,action 提交到sign.html页面 -->
		<form action="sign.html" method="">
				<!-- name='uname'这个不要忘记填,否则不会传递任何值 -->
			用户名:<input type="" name="uname" id="" value="" />
			<input type="submit" name="" id="" value="登录" />
		</form>
	</body>
```



```
//page2
	<body>
		<div></div>
	</body>
	<script type="text/javascript">
		//1.接收传递过来的值,同时截取字符串substrl('',),从[1]开始到最后,空就是默认截取到最后
		var parms = location.search.substr('1');
		//2.分割数据,并赋值到一个新数据里,这里的只取=号两边的值.
		var arr = parms.split('=');
		//3.把得到的值,输出到页面元素中
		var div = document.querySelector('div');
		div.innerHTML = ''+arr[1]+'欢迎您';
		// console.log(arr);
	</script>
```





#### location 对象的方法

| location对象方法   | 返回值                                                       |
| ------------------ | ------------------------------------------------------------ |
| location.assign()  | 跟href 一样,可以跳转页 (也称为重定向页面),可以记录历史,可以后退 |
| location.replace() | 替换当前页面,不记录历史,不能后退页面                         |
| location.reload()  | 重新加载页面,相当于刷新,如果参数为true 强制刷新              |





#### navigator 对象

> navigator 对象包含有关浏览器的信息,它有很多属性,我们最常用的是user Agent,该 属性可以客户机发送服务器的user-agent头部的值.
> 

这是判断用户使用什么终端,并返回不同的版本页面,并进行跳转

```
<script>
        if ((navigator.userAgent.match(/(phone|pad|pod|iPhone|iPod|ios|iPad|Android|Mobile|BlackBerry|IEMobile|MQQBrowser|JUC|Fennec|wOSBrowser|BrowserNG|WebOS|Symbian|Windows Phone)/i))) {
            window.location.href = "../H5/index.html"; //手机
        } else {
         window.location.href = '../index.html';	//pc端
        }
    </script>
```





#### histroy 对象

window对象给我们提供了一个history对象,与浏览器历史记录进行交互,该 对象包含用户(在浏览器窗口中)访问过的url.



| history对象方法 | 作用                                                |
| --------------- | --------------------------------------------------- |
| back()          | 可以后退功能                                        |
| forward()       | 可以前进功能                                        |
| go(参数)        | 前进,后退功能 ,参数:前进一步就是 1 ,后面一步就是 -1 |

使用语法:

> histroy.forward();





# PC 网页特效操作

学习目标

- 说出常见offset 系列属性的作用
- 说出常见 client 系列属性的作用
- 说出常见 scroll 系列属性的作用
- 能够封装简单的动画函数
- 能够写出网页轮播图案例



### 元素偏移量 offset 系列



offset 概述

我们使用offset 系列相关属性可以**动态的**得到目标元素的位置(偏移),大小等.

获取元素**距离带有定位父元素的位置**

获得元素自身的大小(宽\高度)

注意:返回的值都不带单位 



offset 系列常用属性

| offset 系列属性      | 作用                                                     |
| -------------------- | -------------------------------------------------------- |
| element.offsetParent | 返回作为该 元素带有定位的父元素,如果父级没定位则返回body |
| element.offsetTop    | 返回元素相对带有定位父元素上方的偏移                     |
| element.offsetLeft   | 返回元素相对带有定位父元素左方的偏移                     |
| element.offsetWidth  | 返回自身包括padding\boder\content的宽度,返回值不带单位   |
| element.offsetHeight | 返回自身包括padding\boder\content的宽度,返回值不带单位   |



语法

> element.offsetTop



注意:

当元素没有定义宽度时,可以通过offsetWidth 获得宽度,这个宽度是返回当前窗口的大小赋于元素





##### offset 与 style 的区别 

| offset              | style                  |
| ------------------- | ---------------------- |
| offset 只能获取属性 | style 即可获取也可赋值 |

所以获取元素大小\位置 offset 更合适,  改变赋值 style 更合适 



##### 小练习:获取鼠标在元素内的坐标位置

```
<body>
	<div class="box">
	</div>
</body>
<script type="text/javascript">
	var box = document.querySelector('.box');
	box.addEventListener('mousemove', function(e) {
		var x = e.pageX - box.offsetLeft;
		var y = e.pageY - box.offsetTop;
		box.innerHTML = 'X坐标是:' + x + 'y坐标是:' + y;
	})
</script>

```



案例练习:拖动登录框随鼠标移动

```
		//1.获取元素,点击按钮,模态框 ,关闭按钮,遮罩层
		var onbtn = document.querySelector('.model');
		var box = document.querySelector('.box');
		var closeBtn = document.querySelector('.close');
		var title = document.querySelector('.title');
		var mask = document.querySelector('.mask-bg');

		//点击按钮1,弹出遮罩层
		onbtn.addEventListener('click', function() {
			mask.style.display = 'block';
			box.style.display = 'block';
		})
		//点击关闭按钮 ,隐藏遮罩层
		closeBtn.addEventListener('click', function() {
			mask.style.display = 'none';
			box.style.display = 'none';
			box.style.left = '50%';
			box.style.top = '50%';
		})

		//2.鼠标按下时,得到鼠标在盒子内的坐标
		title.addEventListener('mousedown', function(e) {
			//这里记录鼠标在盒子里的坐标值,
			var x = e.pageX - box.offsetLeft;
			var y = e.pageY - box.offsetTop;
			// (2) 鼠标移动的时候，把鼠标在页面中的坐标，减去鼠标在盒子内的坐标就是模态框的left和top值
			document.addEventListener('mousemove',move);
			function move(e) {
				box.style.left = e.pageX - x +'px';
				box.style.top = e.pageY - y +'px';
			}
			// (3) 鼠标弹起，就让鼠标移动事件移除
			document.addEventListener('mouseup',function () {
				document.removeEventListener('mousemove',move);
			})
		})
```

核心思路:

鼠标的坐标 减去 鼠标在盒子内的坐标 ,才是模态框真正的位置.





### 元素可视区 client 系列

> client 客户端,使用client 系列的相关属性,获取元素可视区的相关信息通过这些属性可以动态的得到该元素的边框大小\元素大小等

| client 系列属性      | 作用                                                      |
| -------------------- | --------------------------------------------------------- |
| element.clientTOP    | 返回元素的上边框的大小                                    |
| element.clientLeft   | 返回元素的左边框的大小                                    |
| element.clientWidth  | 返回自身包括padding\boder\content的宽度,不含边框,不带单位 |
| element.clientHeight | 返回自身包括padding\boder\content的高度,不含边框,不带单位 |



### 元素滚动 scroll 系列



> 使用scroll 系列,可以获取滚动相关属性,得到该元素的大小\滚动距离等

| scroll系列属性       | 作用                                                      |
| -------------------- | --------------------------------------------------------- |
| element.scrollTOP    | 返回被卷去的上侧距离                                    |
| element.scrollLeft   | 返回被卷去的左侧距离                                       |
| element.scrollWidth  | 返回自身实际的宽度,包含padding,内容,不含边框,不带单位 |
| element.scrollHeight | 返回自身实际的高度,包含padding,内容,不含边框,不带单位 |

##### 练习，滚动改变侧栏的位置
```
<div class="contaier">
			<div class="bannr1"></div>
			<div class="bannr2"></div>
			<div class="bannr3">banner3</div>
			<div class="bannr4">main</div>
			<div class="bannr5"></div>
		</div>
			<div class="sliderbar">
				<span>back</span>
			</div>
	</body>
	<script type="text/javascript">
		//1.获取slide 
		var slide = document.querySelector('.sliderbar');
		var banner3	= document.querySelector('.bannr3');
		var main = document.querySelector('.bannr4');
		var goback = document.querySelector('span');
		var mainTop = main.offsetTop;
		//这个TOP值就是目标距离 
		var bannertop = banner3.offsetTop;
		//slide滚动到位置时，固定不跳的数值.
		var sliderTop = slide.offsetTop - bannertop;
		// console.log(sliderTop);
		// console.log(banner3.offsetTop);
		//2.添加页面滚动事件 scroll
		document.addEventListener('scroll',function () {
			// console.log(window.pageYOffset);
			if(window.pageYOffset >=bannertop){
				slide.style.top = sliderTop + 'px';
				slide.style.position = 'fixed';
			} else {
				slide.style.top = '360px';
				slide.style.position = 'absolute';
			}
			if(window.pageYOffset >= mainTop){
				goback.style.display = 'block';
			}else{
				goback.style.display = 'none';
			}
		})
	</script>
```

​	



### 小结
三大系列总结
1. offset 系列经常用于获得元素位置 offsetTop  offsetLeft
2. client 系列经常用于获得元素大小 clientWidth ClienHeight
3. scroll 系列经常用于获得滚动距离 scrollTop scrollLeft



### mouseover 与 mouseenter 区别

mouseenter 鼠标事件

- 当鼠标移动到元素上时就会触发mouseenter 事件
- 类似mouseover,它们两者之间的差别是：
- mouseover 鼠标经过自身盒子会触发 ，经过子盒子还会触发。
- mouseenter **只会经过自身盒子触发** 
- 之所以这样，就是因为mouseenter不会冒泡



### 动画函数封装

> 核心原理：通过定时器 seInterval()不断移动盒 子位置

实现步骤：
- 获得盒子当前位置
- 让盒子在当前位置加1个移动距离
- 利用定时器不断重复这个操作
- 加一个结束定时器的条件
- 注意此元素需要添加定位，i才能使用element.style.left

###### 练习1：移动盒子

```
		<div class="box"></div>
		<script type="text/javascript">
			// 实现步骤：
			// - 获得盒子当前位置
			// - 让盒子在当前位置加1个移动距离
			// - 利用定时器不断重复这个操作
			// - 加一个结束定时器的条件
			// - 注意此元素需要添加定位，i才能使用element.style.left
			var box = document.querySelector('.box');
			var star = document.querySelector('.star');
			var timer = setInterval(function() {
				if (box.offsetLeft >= 100) {
					clearInterval(timer);
				}
				box.style.left = box.offsetLeft + 1 + 'px';
			}, 30);
		</script>
```

#### 动画函数的简单封装

```
function animate(obj,target,times){	//自定义形参
	var timer = setInterval(function() {
		if (obj.offsetLeft >= target) {
			clearInterval(timer);
		}
		obj.style.left = obj.offsetLeft + 1 + 'px';
	}, times);
}
animate(box1,300,30);//传实参
```

优化方案1

为了避免过多的元素同时运行一个函数，会造成开启了多个内存空间的问题，建议给：不同的元素指定不同的定时器
```
function animate(obj,target,times){	//自定义形参
	//这里把元素封装到对象里：就比如：var obj = {}; obj.name = name;
	obj.timer = setInterval(function() {
		if (obj.offsetLeft >= target) {
			clearInterval(obj.timer);
		}
		obj.style.left = obj.offsetLeft + 1 + 'px';
	}, times);
}
animate(box1,300,30);//传实参
```

优化方案2 
在原来的基础上会出现一个bug,如果是用按钮触发 动画函数，执行次数会叠加，所以我们必须让元素始终只有一次定时器在执行，先清除以前的定时器。
```
function animate(obj,target,times){	//自定义形参
	//先清除原先的动画
    clearInterval(obj.timer);
	obj.timer = setInterval(function() {
		if (obj.offsetLeft >= target) {
			clearInterval(obj.timer);
		}
		obj.style.left = obj.offsetLeft + 1 + 'px';
	}, times);
}
animate(box1,300,30);//传实参
```