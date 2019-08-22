- [JSON](#JSON)
	- [JSON分类](#json分类)
	- [JSON中允许的值](#json中允许的值)
	- [JSON.parse()](#json.parse)
	- [JSON.stringify()](#json.stringify)
	- [兼容IE7及以下版本](#兼容ie7及以下版本)

### JSON

- JavaScript Object Notation，其中Notation是JS对象表示法。
- JS中的对象只有JS自己认识，其他的语言都不认识。
- JSON就是一个特殊格式的字符串，这个字符串可以被任意的语言所识别，并且可以转换为任意语言中的对象，JSON在开发中主要用来数据的交互。
- JSON和JS对象的格式一样，只不过JSON字符串中的属性名必须加双引号。

```
        var obj = '{"name":"小猫","age":22,"gender":"女"}';
        console.log(typeof obj);        //string
```

#### JSON分类

- 对象 {}
- 数组 []

#### JSON中允许的值

- 字符串
- 数值
- 布尔值
- null
- 对象
- 数组

#### JSON.parse()

- 可以将以JSON字符串转换为js对象。
- 它需要一个JSON字符串作为参数，会将该字符串转换为JS对象并返回。

```
    var json = '{"name":"小猫","age":22,"gender":"女"}';
    var arr = '[1,2,3,"hello",true]';

    var o = JSON.parse(json);
    var o2 = JSON.parse(arr);
    console.log(o);     //Object
    console.log(o.name);        //小猫
    console.log(o2);        //Array
    console.log(o2[0]);     //1
```

#### JSON.stringify()

- 可以将一个JS对象转换为JSON字符串。
- 需要一个js对象作为参数，会返回一个JSON字符串。

```
        var obj3 = {name:"小花",age:22,gender:"女"};
				
        var str = JSON.stringify(obj3);
        console.log(typeof str);        //strng
        console.log(str);       //{"name":"小花","age":22,"gender":"女"}
```

#### 兼容IE7及以下版本

JSON这个对象在IE7及以下的浏览器中不支持，所以在这些浏览器中调用时会报错。

**解决方式**

引入一个定义好了的json.js文件。