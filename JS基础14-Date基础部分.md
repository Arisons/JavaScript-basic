## Date

> Date是日期类，通过它可以对事件进行处理

```javascript
var time = new Date(); 
//=> 获取当前客户端本机时间（当前获取的事件不能作为重要的参考依据）
//=> 获取的结果是一个日期格式的对象（typeof new Date() -> 'object'）

time.getFullYear(); //=> 获取四位年
time.getMonth(); //=> 获取月份(0-11)
time.getDate(); //=> 获取日
time.getDay(); //=> 获取星期（0-6代表周日~周六）
time.getHours(); //=> 获取小时
time.getMinutes(); //=> 获取分钟
time.getSeconds(); //=> 获取秒
time.getMilliseconds(); //=> 获取毫秒
time.getTime(); //=> 获取当前日期距离`1970-01-01 00:00:00`的毫秒差

```

```javascript
var time = new Date('2018-01-01'); //=> 当new Date中传递一个时间格式的字符串，相当于这个字符串转换为标准格式实践对象格式（转换完成后，就可以调用上面的方法了）

//=> 时间格式字符串
//=> '2018-01-01' （IE下不识别）
//=> '2018/01/01'	
//=> '2017/01/01 17:02:05'
//=> 1532250440860 （如果传递的是距离1970年的毫秒差，也是可以识别转换的，但是只能是数字，不能使字符串）
```

测试：实现倒计时

```javascript
function computed(){
	var nowTime = new Date(),
		targetTime = new Date('2018/12/12 12:12:12');
	var spanTime = targetTime - nowTime;
	if( spanTime <= 0 ){
		return;
	}
	var hour = Math.fllor(spanTime/(1000*60*60));
	spanTime -= hour*60*60*1000;
	var minute = Math.floor(spanTime/(1000*60));
	spanTime -= minute*60*1000;
	var second = Math.floor(spanTime/1000);
	
}
```