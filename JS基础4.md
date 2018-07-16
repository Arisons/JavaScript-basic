## JS中的数据类型
> 基本数据类型（值类型）
> 
> + number: 数字
> + string: 字符串
> + boolean: 布尔
> + null: 空对象指针
> + undefined: 未定义

> 引用数据类型
> 
> + object对象数据类型
>   + {} 普通对象
>   + []  数组
>   + /^$/ 正则
>   + ...
> + function 函数数据类型

```javascript	
12 12.5 -12.5 0
"aa" 'bb' => 单双引号包裹起来的都是字符串（单双引号没有区别）
true false => 布尔类型，只有两个值
null
undefined

{name:'mary',age:'8'}
[12,23,34]
/^-?(\d|([1-9]\d+))(\.\d+)?$/
function fn(){}
```

这么多数据类型JS如何去检测？

- typeof: 检测数据类型的运算符
- instanceof: 检测某个实例是否属于这个类
- constructor: 获取当前实例的构造器
- Object.prototype.toString.call: 获取当前实例的所属类信息（**此方法最为准确**）

**typeof**

> 使用typeof检测，返回的结果是一个字符串，字符串中包含的内容证明了值是属于什么类型
> 
> 【typeof 局限性】
> 
> 1、typeof null不是"null"而是"object";因为null虽然是单独的一个数据类型，但它原本意思是空对象指针，浏览器使用typeof检测的时候会把它按照对象来检测
> 
> 2、 使用typeof无法具体细分出到底是数组还是正则，因为返回的结果都是"object"

```javascript
typeof 12; // =>"number"

var num = 13;
typeof num; // =>"number"

typeof true; // =>"boolean"

typeof 'abcdef'; // =>"string"

typeof undefined; // =>"undefined"

typeof null; // =>"object"

typeof {name:'11'}; // => "object"

typeof function (){}; // =>"function"

typeof []; // =>"object"

typeof /^$/; // =>"object"
```

小测试：

```javascript
console.log(typeof typeof []);
```

## 布尔类型

**`Boolean()`**
> 把其他数据类型的值转换为布尔类型
> 
> 只有`0、NaN、空字符串、null、undefined`这五个数据值转换为布尔类型的false，其余的都会变成true

**`!`**
> !=: 不等于
> 叹号在JS中还有一个作用：`取反`，先把值转换为布尔类型，然后再去取反

**`!!`**
>在一个叹号取反的基础上再取反，取两次反相当于没做操作，但是却已经把其他数据类型转换为布尔类型，和Boolean作用相同

## 字符串

> 在JS中单引号和双引号包起来的都是字符串

## number

> 0 12 -12 12.5，JS中多增加了一个number类型的数据`NaN`
> 
> typeof NaN => "number"

**`NaN`**

> not a number: 不是一个数，但是属于number类型
> 
> NaN == NaN: false， NaN和任何其他值都不相等

**`isNaN()`**
> 用来检测当前这个值是否是非有效数字，如果不是有效数字检测的结果为true，反之则为false 

```javascript
isNaN(0); //=>false
isNaN(NaN); //=>true
isNaN('12'); //=>false 当我们使用isNaN()检测值的时候，检测的值不是number类型的，浏览器会默认的把值转化为number类型然后再去检测

isNaN([]); //=>false
```
 
**`Number()`**
> 把其他数据类型的值转换为number类型的值

```javascript
Number('12'); //=>12
Number('12px'); //=>NaN 在使用Number转换的时候只要字符串中出现任何一个非有效数字字符，最后的结果都是NaN

Number(true); //=>1
Number(false); //=>0

Number(null); //=>0
Number(undefined); //=>NaN

Number([]); //=>0 把引用数据类型转换为number，首先需要把引用数据类型转换为字符串（toString），再把字符串转换为number即可 例如：[] -> '' '' -> 0
Number([12]); //=>[12] -> '12' '12' -> 12
Number([12,23]); //=> [12,23] -> '12,23' '12,23' -> NaN

Number({}); //=> NaN
Number({name:'xyx'}); //=>NaN

```

**`paeseInt()`**

> 把其他数据类型这是转换为number，和Number方法在处理字符串的时候有所区别

```javascript
Number('12px'); //=> NaN
paeseInt('12px'); //=> 12
paeseInt('12px13'); //=> 12 提取规则，从左到右依次查找有效字符，知道遇到非有效数字字符为止（不管后面是否还有，都不找了），把找到的转化为数字

parseInt('px12'); //=>NaN
parseInt('12.5'); //=> 12
```

**`parseFloat()`**

> 在parseInt的基础上可以识别小数点

```javascript
parseInt('12.5px'); //=>12
parseFloat('12.5px'); //=>12.5
```

思考：parseInt常用的只需要传递一个值做参数即可，但它支持多个参数，获取后扩展其他参数的意思

## null和undefined

> null: 空，没有
> undefined: 未定义，没有


> "":空字符串，没有
> 0:也可以理解为没有

`空字符串和null区别`

> 空字符串术语挖了个坑，但是没有种任何东西
> null是连坑都没挖

> 空字符串相对于null来说开辟了内存，消耗了那么一丢丢的性能

`null和undefined的区别`

> null 一般都是暂时没有，与其中以后会有（可能以后也没有达到预期）：在JS中null一般都是手动先赋值为null，后期我们再给其赋值
> 
> undefined 完全没在预料之内的