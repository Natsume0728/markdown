# JS

## 学习一门编程语言的基本步骤

1. 了解背景知识：历史、现状、特点、应用场景
1. 搭建开发环境，编写hello world
1. 变量和常量
1. 数据类型
1. 运算符
1. 逻辑结构
1. 通用小程序
1. 函数和对象
1. 第三方库、框架
1. 实用的项目

[程序员必做50题](https://wenku.baidu.com/view/af66e2f14afe04a1b071de42.html)

## JS概述

1. 历史
   - 1995年，JS出现在Netscape的浏览器中
   - 1997年，JS提交给了ECMA, 出现了ECMAScript标准规范
   - 2009年，JS遵循CommonJS规范，开始向服务器端发展
1. 现状
  既可以运行在客户端浏览器，也可以运行在服务器端NodeJS
1. 特点
   - 解释型语言，编译一行执行一行。
   - 弱类型语言
   - 基于对象
   - 跨平台
1. 应用场景
   - 制作浏览器端的交互效果
   - 创建移动App
   - 创建web服务器、操作数据库等服务器端应用
   - 2D绘图

## JS的执行环境

- 浏览器自带的JS解释器
- NodeJS下的JS解释器  
   在命令行下   node -v  查看当前的NodeJS版本号  

## 执行JS代码

- 浏览器下：  
   创建01_hello.js和01_hello.html  
   把js文件嵌入到html文件中  
\<script src="01_hello.js">\</script>
- NodeJS下：  
   `node C:/xampp/.../01_hello.js`   回车  

## JS语法规范

- 区分大小写
- 每行代码结束的分号可加可不加，习惯都加
- 分为单行注释(//...)和多行注释(/*...*/)  

## 变量

>变量是用于存储数据的容器

- 声明变量
   var x=1;  
   在内存中创建空间，名称叫x；把数据1存放到空间x中。
- 变量的命名规则
  - 变量的名称由字母、数字、美元符号、下划线组成的；不能以数字开头。
  - 多个连词之间命名(驼峰命名、下划线命名)  
  userName  userAge  userPassword  
  user_name  user_age  
  - 不能使用关键字和保留字作为变量名
 ![JS保留关键字.png](https://i.loli.net/2019/07/31/5d41768fe520b62136.png)
- 声明变量未赋值  
   var num;  
  变量声明后未赋值，结果为undefined  
- 一次性声明多个变量  
  var a=1,b=2,c;  
  多个变量之间用逗号隔开。  

## 常量

 一旦声明不能重新赋值  
 例如：圆周率、春节的日期...  
  const PI=3.14;  
  ~~PI=3.14159~~ ==> 报错  

```js
var r=5;
const PI=3.14;
//面积和周长
var area=PI*r*r;
var len=2*PI*r;
console.log(area);       //78.5
console.log(len);       //31.400000000000002
console.log(0.1+0.2);  //0.30000000000000004
```

## 数据类型

 >数据分为原始类型和引用类型
 >>原始类型分为数值型、字符串型、布尔型、未定义型、空

- 数值型 ==> 分为整型和浮点型
  - 整型在内存中占4个字节，浮点型占8个字节  
  八进制  以0开头， 例如 013 -> 11  
  十六进制  以0X开头，  例如  0XA -> 10  
    A~F 代表10~15    不区分大小写  
    0XFF -> 255  
  - 浮点型 ==> 分为普通小数和指数型小数  
    3.14E6   ->  31400000  
    3.14E-6  ->  0.00000314  

typeof  检测数据类型 ==> **返回字符串**  

- 字符串型  
  数据被引号包含就是字符串类型，不区分单双引号  
    **查看任意一个字符的Unicode码**  
      'a'.charCodeAt()   //97  
- 布尔型  
  true/false  
  在程序中表示真或者假  
  一般用于是否的结果，例如是否登录，是否注册，是否在售，是否为会员...  
- 未定义型  
  声明了变量未赋值，结果就是undefined  
- 空——null  
  常和引用类型数据一起使用

## 数据类型转换

### 隐式转换  

- 数字+字符串  
数字转换成字符串  
   1+'2'  ==> '12'
- 数字+布尔型  
 布尔型转成数字  
 true ==> 1 false ==> 0  
   3+true  ==> 4  
   3+false  ==> 3  
- 字符串+布尔型  
布尔型转成字符串  
   '5'+true  ==> '5true'
 JS中加号(+)的作用:
- 执行加法运算
- 执行字符串拼接

#### 减法(-)、乘法(*)、除法(/) 隐式换行

**将运算符两端的数据转为数值型(自动调用Number)**，  
如果转换失败，返回NaN(Not a Number)，  
任何值和NaN执行减乘除运算符都会返回NaN

```js
var str1=1+'2'; // '12'
var str2='3'+'4'; // '34' 
console.log(str2,typeof str2);
var num=3+false;//3
console.log(num,typeof num);//3 'number'
var str3='5'+true;//'5true'
console.log(str3,typeof str3);//'5true' string

// var num1=3,num2=true,num3='tedu';
// console.log(num1+num2+num3);//'4tedu'
// console.log(num2+num3+num1);//'truetedu3'
// console.log(num3+num1+num2);//'tedu3true'


var num1=3-'2'; // 1
var num2=3-true;// 2
var num3='3'*'5';//15
var num4=20/'4'; //5
//隐式将'a'转为数值型，返回NaN
var num5=3-'a';//NaN  'number'
var num6=1-undefined;//NaN  'number'
var num7=2-null;//2
var num8=3+NaN;//NaN 'number'
console.log(num8,typeof num8);
```

### 强制转换

#### 将任意的数据强制转为数值型

- Number()
  - Number('a');   //NaN
  - Number('1');   //1
  - Number('1a');  //NaN
  - Number(undefined);  //NaN
  - Number(null);  //0
  - Number(true);  //1

```js
var num1 = Number('a'); console.log(num1)  //NaN
var num2 = Number(undefined); console.log(num2)  //NaN
var num3 = Number(null); console.log(num3)  //0
var num4 = Number(true); console.log(num4)  //1
var num5 = Number('1a'); console.log(num5)  //NaN
```

#### 将数据转为整型

`parseInt()`  
常用于将字符串或数字转为整型，其它的数据返回NaN；  
如果要转换的字符串以非数字开头，也返回NaN

```js
var num6 = parseInt('3.5'); console.log(num6)  //3
var num7 = parseInt('1a'); console.log(num7)  //1
var num8 = parseInt('a1'); console.log(num8)  //NaN
var num9 = parseInt(undefined); console.log(num9)  //NaN
var num10 = parseInt(true); console.log(num10)  //NaN
var num11 = parseInt(null); console.log(num11)  //NaN
var num12 = parseInt(3.5); console.log(num12)  //3
```

#### 将数据转为浮点型

parseFloat()  
和parseInt的用法基本一致，只是转的数据是浮点型。  
`var num13 = parseFloat('1.5a'); console.log(num13)  //1.5`

#### 数值型和布尔型转为字符串型

 toString()  
 var num=10;  
 num.toString();  // '10'

## 运算符

>表达式: 由运算符连接的操作数据，所组成的形式。
 >>运算符分为算术运算符、比较运算符、逻辑运算符、位运算符、赋值运算符、三目运算符

### 算术运算符

- \+  
- \-  
- \*  
- /  
- %   取余
- ++  自增，在原来的基础之上加1
- --   自减，在原来的基础之上减1

  console.log(num++); 先打印num的值，再执行自增  
  console.log(++num); 先执行自增，再打印num的值  
`var num=3;   console.log(num-- + --num);`  

### 比较运算符

- \>  
- <  
- \>=  
- <=  
- !=  
- ==  
- ===(全等于)  
- !== 全不等于  

  返回一个布尔型的值  

  ==  只是比较两个值是否相等  
  ===  不仅比较值，还会比较类型是否相等  
如果数据类型不同，会发生数据类型转换  
  3>'10'  字符串转成数字10  
  '3'>'10'  两个字符串比较的是Unicode码  
  3>'10a'  //false  
  3<'10a'  //false  
  3=='10a' //false  
      '10a'  -> NaN  
   NaN和任何值比较(> < >= <= == ===)都返回false  
   NaN==NaN  返回false  

### 逻辑运算符

- 或者( || )   关联的两个条件只需要满足其一, 结果是true，否则false
- 并且( && )   关联的两个条件都是true，结果是true，否则false  
- 非(反向) !    !false -> true   !true -> false

  逻辑短路  

- &&  当第一个条件为false的时候，就不需要再执行第二个条件
- ||  当第一个条件为true的时候，就不需要再执行第二个条件

注意：**逻辑短路无需关注最终结果是true还是false，重点是看是否会执行第二个表达式。**  
 var num=3;
 num>5  &&  console.log(a);
 num<1  ||  console.log(a);

### 位运算符(了解)

>在执行运算的时候，计算机会把数据转成二进制进行运算。  

- 按位与( & )  上下两位都是1，结果是1，否则是0
- 按位或( | )  上下两位含有1，结果是1，否则是0
- 按位异或( ^ )  上下两位不同为1，相同为0
- 按位右移( >> )  删除二进制的最后一位或者多位，每次缩小到原来的一半或者更多。
- 按位左移( << )  在二进制的最后添加0，成倍增加

### 赋值运算符

- =  
- +=  
- -=  
- *=  
- /=  
- %=

### 三目运算符

 由三个表达式或者数据组成的形式。  
 条件表达式 ? 表达式1  :  表达式2  
  如果条件表达式为true，执行表达式1  
  如果条件表达式为false，执行表达式2  

## 浏览器端函数

- alert()  弹出警示框(消息框)
- prompt()  弹出提示框(输入框)，需要使用变量来接收输入的值；**值的类型是字符串型**。

## 流程控制

  程序=数据 + 算法  
  程序分为顺序执行、选择执行、循环执行  

- if语句  
if(条件表达式){
   语句;
}
 如果条件表达式为true，会执行后边的语句
 在条件表达式中，有一些值默认转成false
   0、NaN、''、undefined、null
- if-else语句  
if(条件表达式){
  语句1;
}else{
  语句2;
}
 如果条件表达式为true，执行语句1，否则条件表达式为false，执行语句2
如果if或者else后只有一行语句，则后边的大括号可以省略的。

- if-else嵌套  
  用于判断多种情况
if(条件表达式1){
  语句1;
}else if(条件表达式2){
  语句2;
}else ... if(条件表达式n){
  语句n;
}else{
  语句n+1;  //以上所有的条件表达式都是false
}
- switch-case语句  
  是一种特殊的分支语句，可以根据一个表达式的值，来选择执行不同的程序  
switch(表达式){
  case 值1: //如果表达式的值是值1
   语句1;
   break;
   ....
  case 值n:
   语句n;
   break;
  default:
   语句n+1;  //以上所有的表达式和值比较都是false
}
  注意：在case中，表达式和值比较实用的是全等于比较，要求值和类型都满足才是true
 对比if-else嵌套和switch-case语句
  相同点：两者都可以用于多项分支语句
  不同点：if-else既可以判断相等，也可以判断不等的情况，使用范围更广；switch-case只能用于全等于的比较，结构上更为清晰，执行效率相对高。

## 循环

 循环：就是一遍又一遍执行相同或者相似的代码
 循环的要素
   循环条件：重复的次数
   循环体：执行的代码

### while循环 

![while循环.png](https://i.loli.net/2019/08/01/5d424274a512139947.png)

while(循环条件){
  循环体;
}
  break 可以结束任何形式的循环，break执行后，后边所有的循环体和循环条件都不再执行。
 
 《JavaScript高级程序设计》第三版
  
  练习：声明变量保存1个数字，无限循环弹出提示框，输入数字；如果输入的比保存的大，警示框提示'big'，如果输入的比保存的小，警示框提示'small'，否则警示框提示'right'，结束循环。
  03_break.html 
  思路：循环前声明变量保存数字，无限循环的循环体中弹出提示框，获取输入的值，再和之前的变量比较(if-else嵌套)。

### do-while循环

![do-while.png](https://i.loli.net/2019/08/01/5d4242303646e79484.png)

do{
  循环体;
}while(循环条件);
 不管循环条件是否为true，都会先执行一次循环体
 练习：打印100~1之间所有整数
 练习：打印70 75 80 85 90 95 100
 练习：计算1~100之间所有能被3整除的数字的和。
 练习：声明变量保存密码'123456'；无限循环弹出提示框，输入密码，如果输入正确，警示框弹出'login success'，并结束循环 break
  05_dowhile.js  05_dowhile.html

### for循环

for(初始值;循环条件;增量){
  循环体
}
①执行初始值
②判断循环条件
③如果循环条件是true执行循环体，是false结束循环
④如果执行完循环体，执行增量
⑤重新执行第二步

2.break和continue
  break: 结束循环，后续不会再执行其它的循环
  continue: 跳过本次循环体，继续执行下一次循环
  
3.循环嵌套
  while、do-while、for循环三者之间可以相互嵌套

## 函数

 parseInt()/parseFloat()...
 分为系统函数和自定义函数
 自定义函数
   function: 功能体,函数，用于封装反复执行的代码，可以接受若干个数据，返回处理的结果。——饺子机
 (1)创建普通的函数
function 函数名称(){
  函数体; //封装的反复执行的代码
}
 调用
   函数名称()
 练习：使用函数封装1+2的计算结果，调用三次。
 练习：使用函数封装计算1~100之间所有整数的和，并调用三次。
 (2)创建带有参数的函数
function 函数名称(参数列表){//形参 ->形式上的参数
  函数体;
}
 调用
   函数名称(参数列表); //实参 -> 传递的数据
  参数列表：可以是0个或者多个，之间用逗号隔开；创建时的参数称为形参，调用时的参数称为实参，实参会赋值给形参。
  **形参可以理解为是一个变量，只是未赋值，默认是undefined**.
 练习：创建函数，传递1个参数，计算1~任意数字之间的和。
 练习：创建函数，传递2个参数，计算任意两个年份之间的闰年个数。  n1~n2
 (3)带有返回值的函数
function 函数名称(参数列表){
  函数体;
  return 值;
}
 调用
   函数名称(参数列表)
  return表示函数执行后，返回的结果；可以保存下来。
 注意事项：
   ①如果没有return和return后没有值，结果都是undefined
   ②return后的所有代码都不会执行
 练习：创建函数getMax，返回任意两个数字中的最大值。
 练习: 创建函数getMax2，返回任意三个数字的最大值。
 练习：创建函数getStatus，传递状态码，返回对应的中文
  1-等待付款 2-等待发货 3-运输中 4-已签收 5-已取消 其它-无法追踪
 练习：创建函数getDays，传递任意一个年份，返回对应的天数。
2.变量作用域
 (1)作用域
   变量和函数的可访问范围，分为两种
   函数作用域：在函数中使用var关键字声明的变量，只能在函数的内部访问。
   全局作用域：在函数外部使用var声明的变量，可以在任意的位置访问
   注意：在函数内使用var声明的变量是局部变量，不使用var声明的变量是全局变量。
 (2)变量声明提升
   JS程序执行前，会将使用var声明的变量提升到所在作用域的最前边，赋值还是在原来的位置。
3.函数的作用域
  函数的可访问范围，也分为全局作用域和函数作用域。
  (1)函数声明提升
    和变量声明提升一样，JS程序执行前，会将function创建的函数提升到所在作用域的最前边，调用可以在任意合法的位置。
4.递归调用
 在函数的内部调用自身
 递归要有结束的条件，结合return来使用。
 练习：使用递归来计算1~任意数字之间的和。
 
 斐波那契数列
 1  1  2  3  5  8  13   21  34....

## 匿名函数

  没有名称的函数  function(){   }
 (1)创建函数
  函数声明方式
function fn(){    }
  函数表达式方式
var fun=function(参数列表){  函数体  }
此时的变量fun就是函数名称
  对比fun和fun()的区别
   fun() 是函数的调用，返回函数的调用结果
   fun 是函数的名称，对应的是函数的整体结构
 函数声明和函数表达式创建函数的区别
  函数声明存在函数提升，调用可以在任意合法位置
  函数表达式不存在函数提升，必须先创建，再调用
 练习：使用函数表达式创建函数，计算任意两个数字之间所有整数的和，并返回结果。
 (2)匿名函数自调用
  目的：创建局部作用域，防止污染全局。
(function(形参列表){
  函数体中的变量和创建的函数只能在内部使用
})(实参列表);
 (3)回调函数
  将匿名函数以实参形式传递，这个匿名函数就称为“回调函数”；此时的形参就是函数名称，如果要调用匿名函数，只需要   形参名称()
function fn(a){
  //a 就是传递的匿名函数的名称
  a();  //执行传递的匿名函数函数体中的代码
}
fn( function(){ ... } );
  练习：创建函数，传递两个参数，实参都是以匿名函数的形式传递，在匿名函数中分别返回数字；计算两个数字相加的和并打印出来。
  
## 全局函数

 parseInt()  将数据转为整型
 parseFloat()  将数据转为浮点型
 encodeURI()  对一个URL中的中文进行编码
 decodeURI()  对已经编码的URL进行解码
 isNaN() 检测一个值是否为NaN 是->true不是->false
 isFinite()  检测一个值是否为有限值  是->true  不是->false     1/0  Infinity  无穷  无限值
 eval()  执行字符串表达式
 练习：使用弹出提示框输入一组运算，使用eval来执行该运算，并打印出来
  06_eval.js   06_eval.html

## 对象

 是引用类型数据
 对象：是一组属性和方法(功能)的集合
 哪些是对象？
   一个手机: 属性颜色，品牌，尺寸；方法有打电话，发短信，看视频，玩游戏;
   一个汽车：属性颜色，品牌，类型；方法有代步，拉货，载客，撞人;
   一个人: 属性性别，姓名，年龄；方法有说话，工作，写代码....
   万物皆对象
 (1)JS中的对象
  内置对象: JS提供的
  宿主对象: 根据JS不同的执行环境来划分
  自定义对象: 自己创建的对象
 (2)自定义对象
  对象字面量
  内置构造函数
  自定义构造函数
4.使用对象字面量创建对象
  使用大括号{ }创建空对象
  属性名和属性值之间用冒号隔开
  多组属性之间用逗号隔开
  属性名中引号可加可不加，如果含有特殊字符必须加引号
 { 属性名:属性值, ... }
 练习: 创建一个人对象，添加姓名、性别、年龄
 练习：创建一个员工对象，包含编号、姓名、性别、生日、工资、所属部门编号
5.访问对象的属性
  对象.属性名
  对象['属性名']
  可以添加之前不存在的属性；
  如果属性不存在，属性值为undefined
  练习：创建一个电脑对象，包含的属性有屏幕尺寸，品牌，颜色，内存大小；获取品牌的属性值，修改颜色的属性值，添加产地属性。
6.使用内置构造函数创建对象
  new Object();   创建一个空的对象
  需要单独添加每一个属性
   对象['属性名'] = '属性值'
   对象.属性名='属性值'
 练习：使用内置构造函数创建用户对象，包含编号，用户名，密码，邮箱，手机。
7.遍历对象的属性
  访问所有的属性
for(var key in 对象){
  key  对象中所有属性名
  对象[key]  通过属性名找对应的属性值
}
  练习：创建对象，包含若干个成绩属性，遍历对象中属性获取总成绩。
  提前声明sum用于保存总和。
8.对象中的方法
 方法也称为成员方法，对应的是一个匿名函数
var person={
  name:'tom',
  say:function(){
    this.name  //this指代当前所在的对象
  }
};
person.say();  //调用方法

### 检测对象中是否含有某个属性

- 对象.属性名===undefined  true->不存在 false->存在
- 对象.hasOwnProperty('属性名'); true->存在  false->不存在
- '属性名'  in  对象   true->存在   false->不存在

## 数组

 数组是由多个元素组成的集合，每个元素就是一个数据
2.创建数组
 (1)数组字面量
  [元素1,元素2...]
  练习：创建数组，包含多个商品的名称；创建数组，包含多个城市名称
 (2)访问数组中的元素
  数组[下标]   下标是从0开始，第一个元素的下标就是0
 (3)内置构造函数
  new Array(元素1,元素2...);
  new Array(3)  初始化元素个数为3，也可以添加更多个元素
  练习：创建数组，保存若干个课程名称；
  练习：创建数组，初始化长度为5，添加篮球场上的五个位置
 (4)数组的长度
  数组.length   获取数组中元素的个数
   作用：在数组的末尾添加新的元素
   数组[数组.length] = 值;
  练习：创建一个空数组，使用数组长度添加若干个国家名称。
2.数组的分类
  数组分为索引数组和关联数组
  索引数组以0以上的整数作为下标
  关联数组以字符串作为下标，只能单独的添加元素
3.遍历数组
 (1)for-in
for(var key in 数组){
  key  要遍历的下标
  数组[key]  下标对应的元素
}
既可以遍历关联数组，也可以遍历索引数组。
 练习：创建数组，包含有多个学生的成绩，获取总成绩。
 (2)循环
for(var i=0;i<数组.length;i++){
  i  代表下标     0 ~ 数组长度-1
  数组[i]   代表下标对应的元素
}
只能遍历索引数组
 练习：创建数组，包含有多个姓名，把tom全部改成"汤姆"
 练习：创建数组，包含多个姓名，查询tom出现的次数
 练习：创建数组，包含多个数字，获取这组数字的最大值
 练习：创建函数getAvg，传递一个参数(一组工资)，返回工资的平均值
4.数组API(方法)
  (Application Programming Interface)
 API 应用程序编程接口，预定义好的一些方法或者函数
 toString()  将数组中的元素按照逗号组合成字符串
 join('-')  将数组中的元素按照指定字符组合成字符串，默认是逗号
 concat(arr2,arr3)  拼接多个数组
 slice(start, end)  截取数组中的元素，start开始的下标，end结束的下标，不包含end本身，如果是负数表示倒数；返回一个数组。
 练习：创建数组a~g，每个字母是一个元素，分别截取cd，f，b，把截取的结果拼接成一个新的数组。
 splice(start, count, value1,value2...) 删除数组中的元素，start开始的下标，count删除的数量，value删除后插入的元素； 返回删除的元素，原数组会发生变化。
 练习：创建数组a~h，每个字母是一个元素，删除d、e，替换f为m，在下标为1的位置插入字母z
 reverse()  翻转数组中的元素
 sort()  对数组中的元素进行排序，默认按照Unicode码从小到大排序
对数字排序
sort(function(a,b){ 
  return a-b;  //从小到大排序
  // return b-a;  //从大到小排序
})

1.数组API
 push()  往数组的末尾添加元素，返回数组的长度
 pop()  删除数组末尾的元素，返回删除的元素
 unshift()  往数组的开头添加元素，返回数组的长度
 shift()  删除数组开头的元素，返回删除的元素
2.二维数组
 数组中的每个元素也是数组
 var arr=[ [], [], [] .. ]
 访问二维数组中的元素   arr[下标][下标]
3.字符串
 **包装对象**：目的是让原始类型数据像引用类型一样，具有属性和方法。
 JS提供了3种包装对象：String  Number  Boolean
 将任意数据转为字符串
   new String()   **返回对象**，使用和字符没有区别
   String()   **返回字符串**

```js
var str1='hello';
//将数据转成字符串，并返回对象
var str2=new String(1);
console.log(str2,typeof str2);  // [String: '1'] 'object'
console.log(str2+2);  //'12'
//将数组转为字符串，返回字符串
//toString()
var str3=String(true);
console.log(str3,typeof str3);//'true' string
```

 (1)转义字符 —— \
   转换字符的意义
   用法：在要转义的字符前加 \
   \'   将引号转义成普通的字符
   \n  将字符n转义成换行符
   \t   将字符t转义成制表符(tab键效果)
   ...
  练习：打印出现 welcome to chi\na

## 字符串API

- length  获取字符串的长度
- charAt()  获取下标对应的字符，也可以使用数组形式 字符串[下标]
- charCodeAt()  获取某个字符的Unicode码
- indexOf(value, start)  查找某个字符串的下标，value要查找的字符串，start开始的下标，默认是0，如果找不到返回-1
  lastIndexOf(value)  查找某个字符串最后一次出现的下标，找不到返回-1
  练习：声明变量保存字符串，检测该字符串中是否含有@，如果有打印“合法的邮箱“，否则打印“不合法邮箱”。
  toUpperCase()  将英文字母转为大写
  toLowerCase()  将英文字母转为小写
  练习：声明变量保存4个英文字母，无限循环弹出提示框，输入验证码(不区分大小写)，如果输入正确结束循环。
  06_code.js   06_code.html
  slice(start, end)  截取字符串，start开始的下标，end结束的下标，不包含end本身；如果为负数表示倒数；end为空截取到最后。
  练习：声明变量保存邮箱，分别截取出邮箱的用户名和域名   tom123456@163.com
  substr(start, count)  截取字符串，start开始的下标，count截取的长度，如果count为空截取到最后，start为负数表示倒数
  练习：声明变量保存身份证号，截取出年月日和性别；打印“1998年06月20日 性别女”
    110236199806202589
  substring(start,end)  截取字符串，start开始的下标，end结束的下标，如果end为空截取到最后；如果下标为负数，自动转成0。
  对比slice和substring
  slice中下标允许使用负数，substring会自动将负数转为0；slice中下标的顺序start小于end，substring中下标大小不分顺序
  练习：将一个英文单词的首字母转大写，其余的字母转小写    heLLo   ->  Hello
  split(sep)  将字符串按照指定字符分隔成数组，sep是指定的字符
  练习：使用split分隔邮箱，获取用户名和域名
4.匹配模式(掌握)
 作用：用于查找、替换字符串
 match(value)   用于查找匹配的字符串，返回所有满足条件的元素，组成数组  /china/ig  
  i  -> ignore  忽略大小写
  g -> global   全局查找
 search(value)  用于查找满足条件的第一个字符串的下标，如果找不到返回-1
 replace(value1,value2)  查找并替换，value1要查找的字符串，value2要替换的字符串
5.Math对象
 不需要使用new创建，可以直接使用
 PI  取圆周率
 abs()  取绝对值
 floor()  向下取整
 ceil()  向上取整
 round()  四舍五入取整
 max()  取一组数字的最大值
 min()  取一组数字的最小值
 pow()  求x的y次幂
 random()  取随机数   >=0  <1
 练习：随机产生0~9之间的一个整数。

## Date对象

 用于对日期时间进行存储和计算
 (1)创建Date对象
 new Date('2019/4/18 10:30:40')
 new Date(2019,3,18,10,30,40); //第二个参数月份范围0~11
 new Date()  存储当前的系统时间
 new Date(1500000000000)  存储的是距离计算机元年的毫秒数对应的日期时间  2017-07-14T02:40:00.000Z
 (2)获取Date对象中的日期时间
  getFullYear/getMonth范围0~11/getDate/
  getHours/getMinutes/getSeconds/getMilliseconds
  getDay 范围0~6/ getTime 距离计算机元年毫秒数
 练习：创建Date对象，保存当前系统的日期时间；根据对象打印  2019年04月19日  星期四
 (3)转为本地字符串
  toLocaleDateString()   //年-月-日
  toLocaleTimeString()   //时:分:秒
  toLocaleString()  //年-月-日 时:分:秒
 (4)修改Date对象中的日期时间
  setFullYear/setMonth/setDate/setHours/
  setMinutes/setMilliseconds/setTime
  setTime修改后，可能会影响其它的日期时间
 练习：创建Date对象，保存员工的入职时间'2019/4/18'；3年后合同到期，计算到期时间；合同到期前一个月续签合同，如果是周末，提前到周五，计算续签时间。
   入职时间：2019-4-18
   到期时间：2022-4-18
   续签时间：2022-3-18
2.Number对象
  new Number()  将数据转为数值型，返回对象
  Number()  将数据转为数值型，返回数值
  Number.MAX_VALUE  获取Number的最大值
  Number.MIN_VALUE  获取Number的最小值
  toFixed(n)  保留小数点后n位
  toString(n)  将数值转为字符串，n转换的进制
3.Boolean对象
  new Boolean()   将数据转为布尔型，返回对象
  Boolean()  将数据转为布尔型，返回布尔型
  !!值   隐式将数据转为布尔型
  toString()   将布尔型数据转为字符串
4.错误处理
 Syntax Error: 语法错误，错误的使用了中文，缺少括号等; 出现后所有的代码都不执行
 References Error: 引用错误，使用了未声明的变量，属于运行时的错误，影响后续代码的执行
 TypeError: 类型错误，错误的使用了数据，例如把变量、数组当做函数使用，属于运行时的错误，影响后续代码的执行
 RangeError: 范围错误，参数的使用超出了范围；属于运行时的错误，影响后续代码的执行
try{
  尝试执行的代码，可能产生错误
}catch(err){
  err 捕获到的错误
  具体处理错误的内容
}
 练习：声明一个变量add未赋值；尝试调用add函数；如果执行错误，给add赋值一个匿名函数，然后再调用add
5.ES6 
 ECMAScript6
 ECMAScript 2015 2016 2017
 http://es6.ruanyifeng.com    《ES6入门》
 (1)块级作用域
  使用let关键字声明的变量，只能在块级作用域下使用，不能被外部访问，不存在变量提升。
  块级作用域：{  }  for、while、do、if....
  防止污染全局
 (2)箭头函数
  是回调函数的另一种写法，和之前的匿名函数不完全一样
 sort( (a,b)=>{
   return a-b;
 } )
 如果箭头函数的函数体中只有一行代码，并且是return形式的，可以简化为  sort( (a,b)=>a-b )
 练习：创建函数add，传递两个参数，每个参数都是回调函数，在回调函数中返回一个数字；在函数add中计算两个数字相加的和。
1.ES6
 (1)函数中的参数
  ES6允许为参数设置默认值，如果没有传递实参，自动调用形参的默认值
 (2)模板字符串
 ` 一组字符串，可以直接写JS  ${js表达式} `
 练习：创建一个对象，保存一个员工的对象(姓名，性别0/1，生日，工资)；使用模板字符串打印员工的信息，性别0显示女，1显示男