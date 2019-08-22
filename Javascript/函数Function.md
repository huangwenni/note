- [函数](#函数)
- [创建函数](#创建函数)
    - [使用构造函数来创建一个对象](#使用构造函数来创建一个对象)
    - [使用函数声明来创建一个对象](#使用函数声明来创建一个对象)
    - [使用函数表达式来创建一个函数](#使用函数表达式来创建一个函数)
- [调用函数](#调用函数)
    - [语法](#语法)
- [立即执行函数](#立即执行函数)
- [函数的方法](#函数的方法)
	- [call方法](#call方法)
	- [apply方法](#apply方法)
- [this情况](#this情况) 
- [arguments](#arguments)
	
### 函数

函数也是一个对象。

函数中可以封装一些功能（代码），在需要时可以执行这些功能（代码）。

使用typeof检查一个函数对象时，会返回function。

封装到函数中的代码不会立即执行。函数中的代码会在函数调用的时候执行。

### 创建函数

#### 用构造函数来创建一个对象（在实际开发中很少使用）

```
var fun = new Function("console.log('Hello 这是我的第一个函数');")
```

#### 使用函数声明来创建一个对象

```
function 函数名([形参1，形参2...形参N]){
    语句...
}
```

```
function fun2(){
    console.log("这是我的第二个函数");
}
```

##### 传入实参

定义一个用来求两个和的函数，可以在函数的（）中来指定一个或多个形参（形式参数）。

多个形参之间使用 “,” 隔开，声明形参就相当于在函数内部声明了对应的变量，但是并不赋值。

实参将会赋值给函数中对应的形参。

```
function sum(a,b){
    console.log(a+b);
}
sum(1,2);
//"3"
```

#### 使用函数表达式来创建一个函数

```
var 函数名 = function([形参1，形参2...形参N]){
    语句...
}
```

```
var fun3 = function(){
    console.log("我是匿名函数中封装的代码");
};
fun3();
```

##### 注意

调用函数时解析器不会检查实参的类型，所以要注意，是否有可能会接收到非法的参数，如果有可能则需要对参数进行类型的检查。

调用函数时，解析器也不会检查形参的数量，多余的参数不会被赋值。

如果实参的数量少于形参的数量，则没有对应实参的形参将是undefined。

函数的实参可以是任意的数据类型。

### 调用函数

当调用函数时，函数中封装的代码会按照顺序执行。

#### 语法

```
函数对象();
fun2();
```

### 立即执行函数

立即执行函数，函数定义完，立即被调用。

立即执行函数往往只会执行一次。

用括号将匿名函数包起来，标识是一个整体，不会报错。

```
(function() {
    alert("我是一个匿名函数");
})();
```

```
(function(a,b) {
    alert("我是一个匿名函数");
})(123,456);
```

### 函数的方法

这两个方法都是函数对象的方法，需要通过函数对象来调用。

当对函数调用call()和apply()都会调用函数执行。

调用call()和apply()可以将一个对象指定为第一个参数，此时这个对象将会成为函数执行时的this。

#### call方法

call()方法可以将实参在对象之后一次传递。

```
        function fun(){
            alert(this.name);
        }
        var obj = {
            name:"obj",
            sayName:function () {
                alert(this.name);
            }
        };
        var obj2 = {name:"obj2"};
        // fun.call(obj);       //弹出obj
        obj.sayName.apply(obj2);        //弹出obj2
```

```
        function fun(a,b){
            console.log("a = "+a);
            console.log("b = "+b);
        }
        var obj = {
            name:"obj",
            sayName:function () {
                alert(this.name);
            }
        };
        fun.call(obj);
        //没传参数
        // a = undefined
        // b = undefined
```

```
        function fun(a,b){
            console.log("a = "+a);
            console.log("b = "+b);
        }
        var obj = {
            name:"obj",
            sayName:function () {
                alert(this.name);
            }
        };
        fun.call(obj,2,3);
        //a = 2
        //b = 3
```

#### apply方法

apply()方法需要将实参封装到一个数组中统一传递。

```
        function fun(a,b){
            console.log("a = "+a);
            console.log("b = "+b);
        }
        var obj = {
            name:"obj",
            sayName:function () {
                alert(this.name);
            }
        };
        fun.apply(obj,[2,3]);
        //a = 2
        //b = 3
```

### this情况

1、以函数形式调用时，this永远都是window。

2、以方法形式调用时，this是调用方法的对象。

3、以构造函数的形式调用时，this是新创建的那个对象。

4、使用call和apply调用时，this是指定的那个对象。

### arguments

在调用函数时，浏览器每次都会传递两个隐含的参数。

1、函数的上下文对象this。

2、封装实参的对象arguments。

arguments是一个类数组对象，它也可以通过索引来操作数据，也可以获取长度。在调用函数时，我们所传递的实参都会在arguments中保存(封装实参)。

arguments.length可以用来获取实参的长度。即使不定义形参，也可以通过arguments来使用实参：

arguments[0]表示第一个实参，arguments[1]表示第二个实参。

它里边有一个属性叫callee,这个属性对应一个函数对象，就是当前正在执行的函数的对象。

```
        function fun() {
            //console.log(arguments instanceof Array);      //false
            //console.log(Array.isArray(arguments));      //false 检查一个对象是不是数组
            //console.log(arguments.length);        //2
            //console.log(arguments[0]);      //hello
            console.log(arguments.callee == fun);      //true
        }
        fun("hello",true);
```