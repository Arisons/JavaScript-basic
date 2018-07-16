## JS组成部分

> ECMAScript(ES): 规定了JS的一些基础核心的知识（变量、数据类型、语法规范、操作语句等）
> DOM: document object model 文档对象模型，里面提供了一些属性和方法，可以让我们操作页面中的元素
> BOM: brower object model 浏览器对象模型，里面提供了一些属性和方法，可以让我们操作浏览器

## 变量和常量

>变量：值是可以变的
>常量：值是不可变的

```javascript
// =>JS中定义变量的方式
// var 变量名 = 值; （ES6中定义变量使用let）

var num = 12;
var str = 'aaaa';

// =>JAVA等后台语言定义变量比较严谨，JS比较松散
// int num = 12;
// float num = 12.5;
// double num = 3.141592654;

console.log(num); //=> 变量其实只是一个无意义的名字，它所代表的的意义都是其存储的那个值

num = 13; //=> 让原有的num变量存储的值修改为13（变量只能代表一个值）
```

```javascript
//=> 任何一个具体的数据值都是常量，例如：12就是一个常量

//=> 和变量类似，我们设置一个常量（也是一个名称），给其存储一个值，但是这个存储的值不能修改
const nn = 12; //=> 定义一个变量nn，给它存储了数值12
nn = 13; //=> Uncaught TypeError: Assignment to constant variable.（常量存储的值是不能修改的）
```

## JS中的命名规范
1、JS中严格区分大小写

```javascript
var test = 'aa';
var Test = 'bb';
console.log(test); //=>aa test和Test是两个不同的变量
```

2、遵循国际命名规范：`驼峰命名法`
> 第一个单词的首字母小写，其余每一个有意义单词首字母大写

```javascript
var studentInfo;

// 命名使用英文单词，不要使用拼音
// 不是所有单词都能简写，我们需要保证大家看到名字后知道所代表的的意思

info: information 信息
init: Initialization 初始化
add / insert / creat ：增加创建插入
remove / rm / clear / del / delete :删除
update: 修改
get / query / select :查询获取
```

3、命名的时候可以使用`$、_、数字、字母`，但是数字不能作为名字的第一位

```javascript
var student_info;
var $xxx; //=> 一般都是应用JQ获取的值
var _xxx; //=> 一般这样的情况代表变量是一个全部或者公用的情况
```

4、JS中很多次都是有特殊含义的，我们把这些词叫做`关键字`；现在没有特殊含义，以后可能会作为关键词的，我们叫做`保留字`；而关键字和保留字都不可以随便来命名；



