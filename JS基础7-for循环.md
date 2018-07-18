## for循环

```javascript
for(设置循环起始值;设置循环执行的条件;步长累加) {
	//=> 循环体，重复做的事情都在循环体中
}
```

```javascript
//1、设置初始值
//2、验证条件
//3、条件成立，执行循环体：不成立，循环解释
//4、步长累加
for(var i=0;i<5;i+=1){
	console.log(i); //=> 0 1 2 3 4 
}
console.log(i); //=>5
```

```javascript
var i = 0;
for(;i<5;){
	console.log(i); //=>没有步长累加，我们的i永远是0，循环条件永远成立“死循环”；项目中不能出现死循环，一旦出现，循环下面的事情都做不了
}
console.log(i); //=>0
```

```javascript
for(var i=0;i<5;i+=2){
	console.log(i);
	continue; //=>结束本轮循环，继续执行下次循环;循环体中continue后面的代码都不会执行，它会直接的去执行步长，然后进入到下一轮
	...
}
console.log(i);
```

```javascript
for(var i=0;i<5;i+=2){
	console.log(i);
	break; //=>结束整个循环：循环体中一旦遇到break，首先后面代码不执行了，而且步长累加也不执行了，循环都结束了
	...
}
console.log(i); //=>0
```

小测试：

```javascript
for(var i=1;i<10;i+=2){
	if(i<5){
		i++;
		continue;
	}else{
		i+=3;
		break;
	}
	console.log(i);
}
console.log(i);
//=>输出几次，结果分别是多少？
```

### **`实现隔行换色`**

```javascript	
var dli = document.getElementsByTagName('li');
var length = dli.length;
var color = null;
for(var i=0;i<length;i+=1){
  if(i%2 === 0){
    color = 'purple';
  }else{
    color = 'pink';
  }
  dli[i].style.backgroundColor = color;

}
```

这里的隔行换色的代码，可以使用冒号表达式或者switch case替换。

[点击查看-示例代码](https://codepen.io/smileyby/pen/NBrByY)

思考：如何实现隔n行换色？
