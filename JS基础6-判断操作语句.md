## 判断操作语句

### **`if/else if/else`**

```javascript
if(条件1) {
	//=> 条件1成立执行操作
} else if(条件2) {
	//=> 上面条件不成立，条件2成立，执行的操作
} else {
	//=>以上条件都不成立执行的操作
}

// 如果好几个条件都成立，只把第一个成立的条件执行，后面成立的条件忽略

// if(A){} 先把A转换为布尔类型，判断真假以此来决定条件是否成立

// if(A>B && A<10){} 只有两个条件都是真，整体条件才是真

// if(A>B || A==0){} 只要其中一个小条件成立，整体条件就是真
```

小测试：

```javascript
var num = parseFloat('width:12.5px');
if( num == 12.5 ){
	alert(12.5);
} else if( num == NaN ) {
	alert(NaN);
} else if(typeof num == 'number') {
	alert(0);
} else {
	alert('空空');
}
```

### **`三元运算符`**

> 条件?条件成立执行:条件不成立执行
> 
> if(条件){}else{}：三元运算符就是这种简单if、else的另一种写法

```javascript
var num = 10;
if(num>5 && num<=10){
	num++;  //=> num+=1 num=num+1 自身累加1
} else {
	num--;  //=> 自身减1
}

//=> 改写成三元运算符
num>5 && num<=10?num++:num--;

num>5 && num<=10?num++:; //=> Uncaught SyntaxError: Unexpected token ;

//=> 改写成三元运算符，如果条件成立或者不成立的某一种情况并不需要做什么处理，我们空着语法不符合，我们使用null、undefined、void(0)（就是undefined）占位即可
num>5 && num<=10?num++:null;

if(num>5 && num<=10){
	num++; 
	console.log(num); 
}

//=> 改写成三元运算符：某一种情况执行多操作，使用小括号包起来，中间用逗号分隔
num>5 && num<=10?(num++,console.log(num));:null;

//=>改写成三元运算符：在三元运算符的操作中不能出现break、continue、return这些关键词，我们无法用三元运算符，我们无法用三元运算符代替if、else

num>5 && num<=10?(num++,return);:null; //=> Uncaught SyntaxError

```

### **`switch case`**

> switch case应用于if、else中一个变量在不同值情况下的不同操作

```javascript
var num = 10;
switch(num){ //=>switch后面小括号存放的是一个值（一般我们都写变量:把变量存储的值拿来用，有时候也可能是一个计算）
	
	case 1:
		...
		break;
	case 5:  //=>case后面放入的都是值，目的是验证switch后面的值和哪一种case后面的值相等，相等的进行对应的处理
		...
		break;
	default: //=> switch后面的值和每一种case情况对应的值都不相等，执行最后的default，类似于else
		...

}
```

示例：

```javascript
var num = 5;
switch(num%2){ //=> 先把取余操作进行运算，拿运算结果和case比较
	case 0：
		num++;
		break;
	case 2-1; //=> case后面也应该是值，此处先把2-1计算，把计算的结果heswitch值比较
		num--;
		//=> 最后一项可以不加break，不加也可以跳出判断
}
```

```javascript
var num=6;
switch(num%3) {
	case 0:
		num++;  //=>不加break，不管后面的条件是否成立，都会继续向下执行，直到遇到break为止。
	case 1: 
		num--;
		break;
	default: 
		num=0;
}

//=> 小应用：把符合某几项值都去做同一件事情，使用不加break实现
switch(num%3){
	case 0:
	case 1: //=>余数是0和1都执行减减的操作
		num--;
		break;
	default:
		num=0;
}
```

```jvascript
var num = '6';
switch(num%3){
	case 0:
		num++;
		break;
	case 6: 
		num--;
		break;
	default:
		num=0;
}
// num结果为0
```

**switch case中的比较使用的是：===**

=：赋值，等号左边是变量，右边是值
==：比较，如果左右两边的值的类型不一样，浏览器会默认转换为一样的然后在进行比较
'6'==6 => '6'->6 6==6 =>true
===：绝对相等，不仅要求值一样，并且类型也要完全一样
'6'===6 =>fasle




