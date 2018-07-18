## 选项卡

```html
<!doctype html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport"
          content="width=device-width, user-scalable=no, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>选项卡</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            font-size: 14px;
        }

        ul {
            list-style: none;
        }

        #tabBox {
            margin: 20px auto;
            width: 500px;
        }

        #tabBox ul {
            position: relative;
            top: 1px;
        }

        #tabBox ul:after {
            content: '';
            display: block;
            clear: both;
        }

        #tabBox ul li {
            float: left;
            margin-right: 10px;
            padding: 0 10px;
            height: 35px;
            line-height: 35px;
            border: 1px solid #999;
            background-color: #ccc;
            cursor: pointer;
        }

        #tabBox div {
          display: none;
          height: 150px;
          line-height: 150px;
          text-align: center;
          border: 1px solid  #999;
        }

        #tabBox div.select {
          display: block;
        }

        #tabBox ul li.select {
          background-color: #fff;
          border-bottom-color: #fff;
        }
    </style>
</head>
<body>
<!-- div#tabBox>(ul>li*3)+div*3 tab 生成如下代码 -->
<div id="tabBox">
    <ul>
        <li class="select">新闻</li>
        <li>电影</li>
        <li>音乐</li>
    </ul>
    <div class="select">世界杯法国夺冠</div>
    <div>一出好戏</div>
    <div>路灯下的小女孩</div>
</div>
<script>
var tabBox = document.getElementById('tabBox'),
    oList = tabBox.getElementsByTagName('li'),
    oDivList = tabBox.getElementsByTagName('div');

//=> 创建一个函数实现页卡切换的功能
function change(index) {
  //=> index:形参，实现方法的时候我们不知道用户点击的哪一个li，设定一个入口，当用户点击需要页卡切换的时候，只需要执行change放阿飞，并且把点击这个li的索引传递给我们，我们就可以再oList集合中通过索引获取到当前点击的这个li对象

  //=> 让所有的li和div移除select样式类
  for(var i = 0; i < oList.length; i += 1){
    oList[i].className = '';
    oDivList[i].className = '';
  }

  //=> 让当前点击的这个li有选中样式
  oList[index].className = 'select';
  oDivList[index].className = 'select';
}

//=> 给每一个li绑定点击事件，点击的时候执行change方法，把当前点击li索引传递进来，实现页卡切换
//for(var i = 0; i < oList.length; i += 1){
  //oList[i].onclick = function(){
    //console.log(i); //=> 不管点击哪一个li输出的结果都是3，也就是此处的i并不是想象中点击的这个li的索引？
    // change(i);
  //};

  //=>解析
  //oList[0].onclick = function(){
    //"console.log(i);" //=> 给元素点击事件绑定方法，点击才执行，此处绑定属于创建函数，空间中存储的都是字符串，i不是变量而是字符
  //}
//}

//=> 自定义属性
for(var i = 0; i < oList.length; i += 1){
  oList[i].index = i;
  oList[i].onclick = function(){
    change(this.index);
  }
}

//=>闭包实现
// for(var i = 0; i < oList.length; i += 1){
//   function(i){
//     oList[i].onclick = function(){
//       change(i);
//     }
//   }(i)
// }

// for(var i = 0; i < oList.length; i += 1){
//     oList[i].onclick = (function(){
//       return function(){
//         change(i);
//       }
//     })(i);
// }

//=> ES6实现
// for(let i = 0; i < oList.length; i += 1){
//     oList[i].onclick = function () {
//       change(i);
//     }
// }

</script>
</body>
</html>
```