`[context].getElementsByTagName()`

> 在指定上下文[context]中，通过元素的标签名来获取一族元素

```javascript
var newList = document.getElementsByTagName('li');
//=> 获取的结果也是一个对象数据类型的值
//=> 1.以数字为属性名，每一个属性存储的都是获取到的每一个li，JS中我们把数字属性名叫做“索引”（索引是逐级递增的）

newList[0] 获取第一个li
newList[1] 获取第二个li
newList[n] 获取第n+1个li

//=> 2.有一个length属性存储的是当前集合一共获取了多少个li

//=> 具备以上两个特点特别像数组，但不是数组，所以我们把它称之为类数组
```