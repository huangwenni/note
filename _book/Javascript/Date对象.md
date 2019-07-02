# Date对象

- [Date对象](#date对象)
	- [使用Date对象来表示一个时间](#使用date对象来表示一个时间)
	- [方法](#方法)

### Date对象
#### 使用Date对象来表示一个时间

创建一个Date对象，如果直接使用构造函数创建一个Date对象，则会封装为当前代码执行的时间。
```
        var d = new Date();
        console.log(d);     //2019-06-04T09:15:58.816Z
```
创建一个指定的时间对象。需要在构造函数中传递一个表示时间的字符串作为参数，日期格式 —— 月份/日/年 时：分：秒。
```
        var d2 = new Date("12/03/2016 11:10:30");
        console.log(d2);        //Sat Dec 03 2016 11:10:30 GMT+0800
```
### 方法
**getDate()**

获取当前日期对象是几日。

**getDay()**

获取当前日期对象是周几。0表示周日，1表示周一。

**getMonth()**

获取当前时间对象的月份。

会返回一个0-11的值。0表示1月，1表示2月。

**getFullYear()**

获取当前日期对象的年份。

**getTime()**

获取当前日期的时间戳。

时间戳，指的是从格林威治标准时间的1970年1月1日，0时0分0秒。到当前日期所花费的毫秒数（一秒 = 1000毫秒）。

计算机底层在保存时间时使用的都是时间戳。
```
        var d2 = new Date("12/03/2016 11:10:30");
        console.log(d2);        //Sat Dec 03 2016 11:10:30 GMT+0800
				
		var date = d2.getDate();
        var day = d2.getDay();
        var month = d2.getMonth();
        var year = d2.getFullYear();
        var time = d.getTime();
        console.log(date);      //3  当前日期是几日
        console.log(day);       //6  当前日期是周几
        console.log(month);     //11
        console.log(year);      //2016
        console.log(time);
```
**Date.now()**

获取当前的时间戳。
```
        var time = Date.now();
        console.log(time);
```
利用时间戳来测试代码的执行性能。
```
        var start = Date.now();
        for (var i = 0;i<100;i++){
            console.log(i);
        }

        var end = Date.now();
        console.log(end - start);
```



