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

## for in 循环

> for in: 用来遍历（循环）对象键值对


```javascript
var obj = {name:'mike',age:'18',friends:'3',weight:'65Kg'};

//=> 对象中有多少组键值对，我们的for in 循环就遍历多少次（一般情况下）
//=> 每一次循环key这个变量存储的都是当前循环这组键值对的属性名
//=> key存储的值都是字符串格式的（不管属性名是否为数字）
//=> 在for in循环遍历的时候，大部分浏览器都是先把对象中的键值对进行排序（把数字属性名排在前面，并且排列的时候按照数字由小到大排列），其次在把非数字的属性名按照之前编写的顺序排列，循环的时候按照重新排列的顺序一次遍历（小数算作字母不算做数字）
for (var key in obj) {
	console.log(key);
	console.log(obj.key); //=> 获取obj中key这个属性对应的属性值 -> undefined 等价于 obj['key']

	console.log(obj[key]); //=> 每一次循环把key变量存储的值（当前遍历的属性名）获取到放在中括号中，获取obj对应属性的属性值
	// obj['name']
	// obj['age']
	// obj['friends']
	// obj['weight']

    // obj['key'] obj.key: 属性名是key
	// obj[key]: 属性名不是key而是可以变量存储的值
}
``` 

**`itar + tab` 快捷创建for循环**

**`itin + tab` 快捷创建for in循环**
