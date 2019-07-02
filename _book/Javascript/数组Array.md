- [Array创建数组](#array创建数组)
	- [向数组中添加元素](#向数组中添加元素)
	- [读取数组中的元素](#读取数组中的元素)
	- [获取数组的长度length](#获取数组的长度length)
	- [修改length](#修改length)
	- [向数组的最后一个位置添加元素](#向数组的最后一个位置添加元素)
- [使用字面量来创建数组](#使用字面量来创建数组)
- [使用构造函数来创建数组](#使用构造函数来创建数组)
- [四个常用的数组方法](#四个常用的数组方法)
	- [push、pop、unshift、shift方法](#push、pop、unshift、shift方法)
	- [数组练习-for循环遍历数组](#数组练习-for循环遍历数组)
- [其他数组方法](#其他数组方法)
	- [slice从数组提取指定元素](#slice从数组提取指定元素)
	- [splice删除数组中的指定元素](#splice删除数组中的指定元素)
		- [数组练习-去除数组中重复的数字](#数组练习-去除数组中重复的数字)
	- [concat、join、reverse、sort方法](#concat、join、reverse、sort方法)

### Array创建数组
数组也是一个对象。它和普通的对象功能类似，也是用来存储一些值的。

不同的是普通对象是使用字符串作为属性名的,而数组是使用数字来作为索引操作元素。

数组的存储性能比普通对象要好，在开发中我们经常使用数组来存储一些数据。

**索引**

从零开始的整数就是索引。
```
        var obj = new Object();
        obj.name = "小猫";

        //创建数组对象
        var arr = new Array();
        //使用typeof检查数组时，会返回object
        console.log(typeof arr);        //object
```
#### 向数组中添加元素
```
数组[索引] = 值 ;
```
```
        arr[0] = 10;
        arr[1] = 33;
        arr[2] = 22;
        console.log(arr);		//Array(3) [ 10, 33, 22 ]
```
#### 读取数组中的元素
如果读取不存在的索引，他不会报错，会返回undefined。
```
数组[索引];
```
```
       var arr = new Array();
       arr[0] = 10;
       arr[1] = 33;
       arr[2] = 22;
       console.log(arr[0]);        //10
       console.log(arr[3]);        //undefined
```
#### 获取数组的长度length
可以使用length属性来获取数组的长度（元素的个数）。

对于连续的数组，使用length可以获取到数组的长度（元素的个数）。

对于非连续的数组，使用length会获取到数组最大的索引+1，尽量不要创建非连续的数组。

```
数组.length;
```
#### 修改length
如果修改的length大于原长度，则多出部分会空出来，如果修改的length小于原长度，则多出的元素会被删除。
```
        var arr = new Array();
        arr [0] = 21;
        arr [1] = 22;
        arr [2] = 23;
				arr.length = 10;
        console.log(arr.length);        //10
```
```
        var arr = new Array();
        arr [0] = 21;
        arr [1] = 22;
        arr [2] = 23;
        arr.length = 1;
        console.log(arr.length);        //1
        console.log(arr);       //Array [ 21 ]
```
#### 向数组的最后一个位置添加元素
```
数组[数组.length] = 值;
```
```
        var arr = new Array();
        arr [0] = 21;
        arr [1] = 22;
        arr [2] = 23
        arr [3] = 50;
        arr [4] = 60;
        arr[arr.length] = 70;
        console.log(arr.length);    //6
        console.log(arr);		    //Array(6) [ 21, 22, 23, 50, 60, 70 ]

```
### 使用字面量来创建数组
```
        var arr = [];
        console.log(typeof arr);        //object
```
**使用字面量创建数组时，可以在创建时就指定指定数组中的元素**
```
        var arr = [1,2,3,4,5,10];
        console.log(arr[3]);        //4
```
### 使用构造函数来创建数组
使用构造函数创建数组时，也可以同时添加元素，将要添加的元素作为构造函数的参数传递。（很少用）
```
        var arr = [1,2,3,4,5,10];
        var arr2 = new Array(10,20,30);
        console.log(arr2);      //Array(3) [ 10, 20, 30 ]
```
```
        var arr = [1,2,3,4,5,10];
        var arr2 = new Array(10,20,30);
        console.log(arr2);      //Array(3) [ 10, 20, 30 ]

        //创建一个数组，数组中只有一个元素10
        arr = [10];
        console.log(arr);       //Array [ 10 ]
        console.log(arr[0]);       //10

        //创建一个长度为10的数组
        var arr2 = new Array(10);
        console.log(arr2.length);       //10
```
**数组中的元素可以是任意的数据类型**
```
        var arr = [1,2,3,4,5,10];
        arr = ["hello",1,true,null,undefined];
        console.log(arr);       //Array(5) [ "hello", 1, true, null, undefined ]
```
**数组中的元素可以是对象和函数**

**数组中也可以放数组，称为二维数组**
```
        //也可以是对象
        var arr = ["hello",1,true,null,undefined];
        var obj = {name:"小猫"};
        arr[arr.length] = obj;
        console.log(arr[5]);

        arr = [{name:"小猫"},{name:"小九"},{name:"小樱"}];
        console.log(arr[1].name);       //小九

        //也可以是一个函数
        arr = [function () {alert(1)},function () {alert(2)}];
        console.log(arr);
        arr[0]();       //调用函数对象

        //数组中也可以放数组，称为二维数组。
        arr = [[1,2,3],[3,4,5],[5,6,7]];
        console.log(arr[0]);        //Array(3) [ 1, 2, 3 ]
```
### 四个常用的数组方法
#### push、pop、unshift、shift方法
**push()**

该方法可以向数组的末尾添加一个或多个元素，并返回数组的新的长度。

可以将要添加的元素作为方法的参数传递，这样这些元素将会自动添加到数组的末尾。

**pop()**

该方法可以删除数组的最后一个元素，并将删除的元素作为返回值返回。

**unshift()**

向数组的开头添加一个或多个元素，并返回数组的长度。

向前边插入元素以后，其他元素的索引会依次调整。

**shift()**

可以删除数组的第一个元素，并将被删除的元素作为返回值返回。
```
    var arr = ["小猫","小九","小樱"];
    var result = arr.push("小梅,","小花");
    console.log("result = " + result);      //result = 5
		
		result = arr.pop();
    console.log(arr);
    console.log("result = " + result);        //result = 小花
		
		console.log(arr);
    result = arr.unshift("小鱼","小草");
    console.log("result = " + result);       //result = 6
		
		result = arr.shift();
    console.log("result = " + result);       //result = 小鱼
```
#### 数组练习-for循环遍历数组
创建一个函数，可以将perArr中的满18岁的Person提取出来，然后封装到一个新的数组中并返回。
```
        function Person(name,age,gender) {
            this.name = name;
            this.age = age;
        }
        //修改Person原型的toString
        Person.prototype.toString = function () {
            return "Person[name = " + this.name + ",age = " + this.age + "]";
        };
        //创建一个Person对象
        var per1 = new Person("小猫",18);
        var per2 = new Person("小九",28);
        var per3 = new Person("小樱",8);
        var per4 = new Person("小梅",16);
        var per5 = new Person("小草",38);
				
        //将这些Person对象放到一个数组中
        var perArr = [per1,per2,per3,per4,per5];
        console.log(perArr);
				
				//arr 形参 要提取信息的数组
        function getAdult(arr) {
        //创建一个新的数组
        var newArr = [];
				
				//遍历arr，获取arr中Person对象
        //判断Person对象的age是否大于等于18，如果大于18就添加到newArr中
        for (var i = 0;i<arr.length;i++){
                var p = arr[i];
                if (p.age>=18) {
                    newArr.push(p);
                }
            }					
            return newArr;
        }
        var result = getAdult(perArr);
        console.log(result);			
```
### forEach遍历数组
不常用，在IE浏览器里只支持IE8以上的浏览器。

需要一个函数作为参数。这种函数，由我们创建但是不由我们调用，称为回调函数。

数组中有几个元素函数就会执行几次,每次执行时浏览器会将遍历到的元素以实参的形式传递进来，我们可以定义形参，来读取这些内容。

**浏览器会在回调函数中传递三个参数**

第一个参数是当前正在遍历的元素。

第二个参数是当前正在遍历的元素的索引。

第三个参数就是正在遍历的数组。
```
        var arr = ["小猫","小九","小樱","小梅","小草"];
        //不建议在全局里创建函数，在这里传一个匿名函数，作用一样
        arr.forEach(function (value,index,obj) {
            console.log(obj == arr);        //true
            console.log(value);
        });
```
### 其他数组方法
#### slice从数组提取指定元素
可以用来从数组提取指定元素。该方法不会改变原数组，而是将截取到的元素封装到一个新数组中返回。

**参数**

1、截取开始的位置的索引,包含开始索引

2、截取结束的位置的索引，不包含结束索引

第二个参数可以省略不写,此时会截取从开始索引往后的所有元素。

索引可以传递一个负值，如果传递一个负值，则从后往前计算（-1倒数第一个，-2倒数第二个）。
```
		//不会改变原数组
        var  arr = ["小猫","小九","小樱","小梅","小草"];
        arr.slice(0,2);
        console.log(arr);       //Array(5) [ "小猫", "小九", "小樱", "小梅", "小草" ]
```
```
        var  arr = ["小猫","小九","小樱","小梅","小草"];
        var result = arr.slice(0,2);        //Array [ "小猫", "小九" ]
        result = arr.slice(0);      //Array(5) [ "小猫", "小九", "小樱", "小梅", "小草" ]
        result = arr.slice(1,-1);   //Array(3) [ "小九", "小樱", "小梅" ]
```
#### splice删除数组中的指定元素
可以用于删除数组中的指定元素，使用splice()会影响到原数组，会将指定元素从原数组中删除，并将被删除的元素作为返回值返回。

**参数**

第一个，表示开始位置的索引。

第二个，表示删除的数量。

第三个及以后可以传递一些新的元素，这些元素将会自动插入到开始位置索引的前面。
```
        var  arr = ["小猫","小九","小樱","小梅","小草"];
        var result = arr.splice(0,2);
        console.log(result);       //Array [ "小猫", "小九" ]
```
```
        var  arr = ["小猫","小九","小樱","小梅","小草"];
        var result = arr.splice(0,1,"小可");
        console.log(arr);   //Array(5) [ "小可", "小九", "小樱", "小梅", "小草" ]
```
##### 数组练习-去除数组中重复的数字
```
        var arr = [1,2,3,2,2,1,3,4,2,5];
        //去除数组中重复的数字
        //获取数组中的每一个元素
        for(var i = 0; i<arr.length;i++){
            console.log(arr[i]);
            //获取当前元素后的所有元素
            for (var j = i+1;j<arr.length;j++ ){
                console.log(arr[j]);
                //判断两个元素的值是否相等
                if (arr[i] == arr[j]){
                    //如果相等则证明出现了重复的元素，删除j对应的元素
                    arr.splice(j,1);
                    //当删除了当前j所在的元素以后，后边的元素会自动部位
                    //此时将会不再比较这个元素，我需要在比较一次所在位置的元素
                   j--;
                }
            }
        }
        console.log(arr);        //1, 2, 3, 4, 5
```
#### concat、join、reverse、sort方法
**concat**

可以连接两个或多个数组，并将新的数组返回。

该方法不会对原数组产生影响。

可以传数组也可以传元素。
```
        var arr = ["小猫","小九","小樱"];
        var arr2 = ["小草","小明","小陈"];
        var arr3 = ["小艾","小花","小梅"];
	    var result = arr.concat(arr2,arr3,"艾猫猫","梅樱九");
        console.log(result);
        //"小猫", "小九", "小樱", "小草", "小明", "小陈", "小艾", "小花", "小梅","艾猫猫","梅樱九"				
```
**join**

该方法可以将数组转换为一个字符串。

该方法不会对原数组产生影响，而是将转换后的字符串作为结果返回。
```
        var arr = ["小妖","小桃","小音"];
        result = arr.join();
        console.log(typeof result);     //string
```
在join()中可以指定一个字符串作为参数，这个字符串将会成为数组中元素的连接符。

如果不指定连接符，则默认使用 ， 作为连接符,传空串 "" 相当于无间隔。
```
        var  arr = ["小妖","小桃","小音"];
        result = arr.join("123);
        console.log(result);     //小妖hello小桃hello小音
```
**reverse**

该方法用来反转数组（前边去后边，后边去前边）。

该方法会直接修改原数组。
```
        var arr = ["小妖","小桃","小音"];
        arr.reverse();
        console.log(arr);       //"小音", "小桃", "小妖"
```
**sort**

可以用来对数组中的元素进行排序。

会影响原数组，默认会按照Unicode编码进行排序。即使对于纯数字的数组，使用sort()排序时，也会按照Unicode编码来排序，所以对数字排序时，可能会得到错误的信息，要自己指定排序的规则。
```
        var arr = ["b","d","e","a","c"];
        arr.sort();
        console.log(arr);       //"a", "b", "c", "d", "e"
```
```
        var arr = [3,4,11,2,5];
        arr.sort();
        console.log(arr);       // 11, 2, 3, 4, 5
```
可以在sort()中添加一个回调函数，指定排序规则。

回调函数中需要定义两个形参，浏览器将会分别使用数组中的元素作为实参去调用回调函数。使用哪个元素调用不确定，但是肯定的是在数组中，a一定在b前面。

浏览器会根据回调函数的返回值来决定元素的顺序，如果返回一个大于0的值，则元素会交换位置。如果返回一个小于0的值，则元素位置不变。如果返回一个0，则认为两个元素相等，也不交换位置。

如果需要升序排列，返回a-b，如果需要降序排列，返回b-a。
```
        var arr = [23,11,15,46,85,25];
        arr.sort(function (a,b) {
            /*
            if(a>b){
                return 1;
            }else if (a<b) {
                return -1;
            }else{
                return 0;
            }
            */
            //升序,效果一样
            return a-b;
        });
        console.log(arr);       //11, 15, 23, 25, 46, 85
```






