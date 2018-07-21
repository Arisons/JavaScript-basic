## 	DOM基础

> DOM: document object model文档对象模型，提供一些属性和方法可以让我们操作DOM元素 

### 获取DOM元素的方法

- document.getElementById 一个元素
- [context].getElementsByTagName 元素集合
- [context].getElementsByClassName 元素集合
- document.getElementsByName 节点集合
- document.documentElement 获取整个HTML对象
- document.body 获取整个body对象
- document.head 获取真个HEAD对象
- [context].querySelector 一个元素对象
- [context].querySelectorAll 获取元素集合

`getElementById`

> 此方法的上下文只能是document
> 
> 一个HTML页面中元素的id理论上是不能重复的
> 
> 1、如果页面中的ID重复了，我们获取的结果第第一个ID
> 
> 2、在IE7及更低版本浏览器中，会把表单元素的name值当做id来使用（项目中尽量不要让表单的name和其他元素的id相同）
> 3、如果我们把JS放在结构下面，我们可以直接使用ID值来获取这个元素（不需要通过getElementById获取）而且这种方式会把页面中所有ID是它的元素都获取到（元素对象/元素集合）=>不推荐

//=> 把当前页面中所有ID叫做box1的都获取到

```javascript
var allTag = document.getElementsByTagName('*'),
	result = [];
for(var i = 0; i < allTag.length; i += 1){
	var item = allTag[i];
	item.id === 'box1'?result.push(item):null;
}
consol.log(result);
```

`getElementsByTagName`

> 上下文可以自己指定
> 
> 获取到的结果是一个元素集合（类数组集合）
> 
> 1、获取的结果是集合，哪怕集合中只有一项，我们想要操作这一项元素（元素对象），需要先从集合中获取，然后再操作

```
<body>
	<div></div>
	<div></div>
	<div></div>
	<div></div>
</body>
<script>
	var bodyBox = document.getElementsByTagName('body')[0];
	bodyBox.getElementsByTagName('div'); //=> Uncaught TypeError: bodyBox.getElementsByTagName is not a function此时的bodyBox是一个类数组集合，我们需要使用的是其中第一项，而不是整个变量
</script>
```

> 2、在指定的上下文中，获取所有子子孙孙元素当中标签名叫做这个的（后代筛选）

```
<div id="box">
	<ul>
		<li></li>
		...
	</ul>
	<div>xxx</div>
</div>
<script>
	var box = document.getElementById('box');
	box.getElementsByTagName('li');
	box.getElementsByTagName('div');
</script>
```

`getElementsByClassName`

> 上下文可以随意制定
> 
> 获取的结果也是一个元素集合（类数组集合）
> 
> 1、真实项目当中，我们经常或通过样式类名来获取元素，getElementsByClassName在IE6-8中不兼容

`getElementsByName`

> 通过元素的name属性值，获取一组元素（类数组：节点集合 NodeList）
> 
> 它的上下文也只能是document
> 
> 1、IE浏览器只能识别表单元素的name属性值，所以这个方法一般都是用来操作表单元素

`document.documentElement / document.body`

> 获取html或body（一个元素对象

```javascript
document.documentElement.clientWidth || document.body.clientWidth //=> 获取当前浏览器窗口可视区域的宽度

//=> clientHeight 获取高度
```

`querySelector / querySelectorAll`

> 在IE6-8下不兼容，而且也没有什么特别好办法处理它的兼容，所以这两个方法多用于移动端开发使用

> querySelector: 获取一个元素对象
> 
> querySelectorAll: 获取的是一个元素集合
> 
> 只要是CSS支持的选择器，大部分都支持

### DOM节点

> node 节点，浏览器认为在一个html页面中所有内容都是节点（包括标签、注释、文本文字等）

> - 元素节点: HTML标签
> - 文本节点: 文字内容（高版本浏览器会把空格和换行也当做文本节点）
> - 注释节点: 注释内容
> - document文档节点
> - ...


`元素节点`
nodeType： 1
nodeName： 大写标签名（在部分浏览器的怪异模式下，我们写的标签名是小写，它获取的就是小写）
nodeValue： null

[curEle].tagName: 获取当前元素的标签名（获取的标签名一般是大写）

`文本节点`
nodeType： 3
nodeName： #text
nodeValue： 文本内容

`注释节点`
nodeType： 8
nodeName： #comment
nodeValue： 注释内容

`文档节点`
nodeType： 9
nodeName： #document
nodeValue： null

> 节点是用来描述页面中每一部分之间关系的，只要我可以获取页面中的一个节点，那么我就可以通过相关的属性和方法获取页面中所有的节点

`childNodes`

> 获取当前元素的所有子节点（节点集合：类数组）
> 注：不仅仅是元素子节点，文本、注释等都包含在内；子节点说明是在儿子辈分中查找

`children`

> 获取所有的元素子节点（元素集合）
> 在IE6-8下获取的结果和标准浏览器中有区别（IE6-8中会把注释节点当做元素节点获取到）

`parentNode`

> 获取当前元素的父节点（元素对象）

`previousSibling nextSibling`

> previousSibling: 获取当前节点的上一个哥哥节点（不一定是元素节点也可能是文本或者注释）
> 
> nextSibling: 获取当前节点的下一个弟弟节点

`previousElementSibling nextElementSibling`

> previousElementSibling: 获取当前节点的上一个哥哥元素节点
> 
> nextElementSibling: 获取当前节点的下一个弟弟元素节点
> 
> IE6-8下不兼容

`firstChild lastChild`

> firstChild: 当前元素所有子节点中的第一个（也不一定是元素节点，可能是文本和注释）
> 
> lastChild: 当前元素所有子节点中的最后一个

> `firstElementChild lastElementChild` (IE6-8不兼容)

### DOM的增删改

> 真实项目中，我们偶尔会在JS中动态创建一些HTML标签，然后把其增加到页面中

`document.creatElement`

> 在JS中动态创建一个HTML标签

`appendChild`

> 容器.appendChild(元素): 把当前创建的元素添加到容器的末尾位置

`insertBefore`

> 容器.insertBefore(新元素,老元素): 在当前容器中，把新创建的元素增加到老元素之前

```javascript
var oDiv = document.createElement('div');
oDiv.id = 'div1';
oDiv.className = 'box';
document.body.appendChild(oDiv);
```

```javascript
//=> 解析一个URL地址每一部分的信息（包含问号传递的参数值）
//=> 1.纯字符串拆分截取
//=> 2.编写正则，捕获到需要的结果
//=> 3.通过动态创建一个A标签，利用A标签的一些内置属性来分别获取
var link = document.creatElement('a');
link.href = 'https://www.baidu.com/s?wd=C%E7%BD%97%E6%8E%A5%E5%8F%97%E5%88%A4%E7%BD%9A&usm=2&ie=utf-8&rsv_cq=%E9%AB%98%E6%99%93%E6%9D%BE+C%E7%BD%97&rsv_dl=0_right_fyb_pchot_20811';
console.dir(link);

//-> hash: 存储了哈希值 
//-> hostname: 存储的是域名
//-> pathname: 存储的是请求资源的路径名称
//-> protocol: 协议
//-> search: 存储的是问号传递参数值，没有传递是空字符串

function queryURLParameter( url ) {
	var link = document.createElement('a');
	link.href = url;
	var search = link.search,
		obj = {};
	if( search.length === 0 ){
		return;
	}
	search = search.substr(1).split(/&|=/g);
	for(var i = 0;i < search.length; i += 2){
		var key = search[i],
			value = search[i+1];
		obj[key] = value;
	}
	link = null;
	return obj;
}
```

`removeChild`

> 容器.removeChild(元素)
> 
> 在当前容器中把某一元素移除掉

`replaceChild`

> 容器.replaceChild(新元素,老元素)
> 
> 在容器中，拿新元素替换老环宇

`cloneNode`

> 元素.cloneNode(false/true)
> 把所有的元素克隆一份一模一样的，false：只可能当前元素本身，true：深度克隆，把当前元素本身以及元素所有后代都进行克隆


