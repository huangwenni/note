- [this](#this)

### this

解析器在调用函数每次都会向函数内部传递一个隐含的参数，这个隐含的参数就是this。

this指向的是一个对象，这个对象我们称为函数执行的上下文对象。

根据函数调用方式的不同，this会指向不同的对象：

1、以函数的形式调用时，this永远都是window。

2、以方法的形式调用时，this就是调用方法的那个对象。

3、当以构造函数的形式调用时，this就是新创建的那个对象。

```
    function fun() {
        console.log(this);
    }
    fun();
    //window
```

```
    var obj = {
        name:"小猫",
        sayName:fun
    };

    console.log(obj.sayName == fun);    //  true
    obj.sayName();                      //以方法形式调用，调用的是对象，Object
    fun();                                     //以函数形式调用，调用的是window，相当于window.fun();
```

```
    function fun() {
        console.log(this.name);
    }
    var obj = {
        name:"小猫",
        sayName:fun
    };

    obj.sayName();      //"小猫"
```

**this可以根据调用者的不同变成不同的值，让程序更加灵活**

```
    var name = "全局";
    function fun() {
        console.log(this.name);
    }
    //创建两个对象
    var obj = {
        name:"小猫",
        sayName:fun
    };
    var obj2 = {
        name:"小九",
        sayName:fun
    };
    obj.sayName();				 //"小猫"
    obj2.sayName();				 //"小九"
```