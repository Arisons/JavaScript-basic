## JS导入的三种方式

> 行内导入JS(慎用：不安全)

```html
<div onclick="alert('测试文本')">点击弹出测试文本</div>
```
> 内嵌式

```html
<script type="text/javascript">alert('弹出测试文本');</script>
```

> 外联式

```html
<script type="text/javascript" src="index.js"></script>
```

**type 不写的话默认就是text/javascript，写上去更规范些。 **

**内嵌式和外联式不能混合使用，如果混合使用则在script脚本快中编写的所有代码都不会被执行。**

**项目中我们一般会把CSS放在body上面，把JS放在body的末尾** ==> body中编写的都是HTML标签，JS很多时候需要操作这些元素，首先我们要保证元素加载成功，才可以在JS中获取到。

如果把JS放在HTML标签前面，如何等到结构加载完成再加载JS？
> JS: window.onload=function(){} 页面中所有资源文件都加载完成执行操作
> 
> JQ: $(document).ready(function(){}) 页面中的结构加载完成就会执行操作 

JQ源码：

```
window.addEventListener('load', function(){},false)/window.attachEvent('onreadystatechange',function(){})
```

1. 写静态页面 => 从UI设计师手中拿到设计稿（静态图片PSD），使用HTML+CSS把图片编程静态的HTML页面
2. 拿JS些一些用户交互的效果，例如，点击一个按钮，实现图片切换等；JS中又有一个很常用的操作就是用来操作页面中的HTML标签（DOM元素）

## JS常用的输出方式

> ### JS中提供的浏览器弹窗 => alert

```js
alert(1);
alert(true);
alert([12,23]);
alert({name:'hehe'}); // "[object Object]"
alert(1+1); //"2"
``` 

**使用alert弹窗提示信息，提示的内容最后都会被转换成字符串（调用toString方法）**

> ### confirm: 在alert基础上增加了让用户选择性的操作（提供两个按钮：确定和取消）

```js
var flag = confirm('确定要删除吗？');

// 用户点击确定按钮时，我们接收到的结果是true，点击取消时我们接收到的结果是false，可更具接收到的结果做不通的处理
// 与alert相同，弹出的内容也会被转成字符串
```

> ### prompt: 在confirm基础上增加用户输入效果

```js
var flag = prompt('确认删除吗？');

// 用户点击取消按钮，我们获取到的结果是null，如果用户点击确定按钮，我们将会获取到用户输入的内容（如果用户没有输入任何内容，获取的姐夫哦是空字符串）
```

**真实项目中，尤其是需要样式精美的网站中，我们的提示框一般都是自己封装常见和组件来实现的，不会用内置的（使用原生JS封装模态框组件）**

> ### console.log(): 控制台输出

console.log(): 在控制台输出，优势不会转换数据类型，输出什么格式的数据都可以

> ### console.dir(): 比LOG输出的更加详细
> ### console.table(): 把JSON数据展示成一个表格

**思考除了上述的输出console里面还有那些输出？**

> ### document.write(): 向页面中打印输出内容

```js
document.write('现在这个输出很少用呢！');
```



