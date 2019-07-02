- [原型Prototype](#原型prototype)

### 原型Prototype
我们所创建的每一个函数，解析器都会向函数中添加一个属性prototype。这个属性对应着一个对象，这个对象就是原型对象。

如果函数作为普通函数调用,prototype没有任何作用。当函数以构造函数的形式调用时，它所创建的对象中都会有一个隐含的属性，指向该构造函数的原型对象。

原型对象就相当于一个公共的区域，所以同一个类的实例都可以访问到这个原型对象。

**通过__proto__来访问该属性**
```
function Person() {

}
function MyClass(){

}
var mc = new MyClass();
var mc2 = new MyClass();
console.log(Person.prototype == MyClass.prototype);     //false
console.log(mc2.__proto__   == MyClass.prototype);   //true
console.log(mc.__proto__   == MyClass.prototype);      //true
```
**当我们访问对象的一个属性或方法时，它会先在对象自身中寻找，如果有则直接使用，如果没有则会去原型对象中寻找，如果找到则直接使用。**
```
function MyClass(){

}
//向MyClass的原型中添加属性a
MyClass.prototype.a = 123;
var mc = new MyClass();
var mc2 = new MyClass();
console.log(mc.a);             //123 mc里没有a，去原型对象找
```
**创建构造函数时，可以将这些对象共有的属性和方法统一添加到构造函数的原型对象中，这样不用分别为每一个对象添加，也不会影响到全局作用域，就可以使每个对象都具有这些属性和方法了。**
```
function MyClass(){

}
//向MyClass的原型中添加属性a
MyClass.prototype.a = 123;
//向MyClass的原型中添加方法
MyClass.prototype.sayHello = function () {
			alert("hello");
}
var mc = new MyClass();
var mc2 = new MyClass();
//向mc中添加a属性
mc.a = "我是mc中的a";
console.log(mc.a);            //我是mc中的a
mc.sayHello();                //弹出hello
```
### hasOwnProperty
可以使用对象的hasOwnProperty()来检查对象自身是否含有该属性
```
       function MyClass() {

       }
       //向MyClass原型中添加一个name属性
       MyClass.prototype.name = "我是原型中的名字";
       var mc = new MyClass();
       console.log(mc.name);        //我是原型中的名字

       mc.age = 18;

       //使用in检查对象中是否含有某个属性时，如果对象中没有但原型中有，也会返回true
       console.log("name" in mc);      //true

       //可以使用对象的hasOwnProperty()来检查对象自身是否含有该属性
       //使用该方法只有对象自身中含有属性时，才会返回true
       console.log(mc.hasOwnProperty("name"));     //false
       console.log(mc.hasOwnProperty("age"));      //true
```
### 原型中的原型
原型对象也是对象，所以它也有原型。

当我们使用一个对象的属性或方法时，会在自身中寻找。

自身中如果有，则直接使用。 如果没有则去原型对象中寻找，如果原型中没有则去原型的原型中寻找，直到找到Object对象的原型。

Object对象的原型没有原型，如果在Object中依然没有找到，则返回undefined。
```
        function MyClass() {

        }
        MyClass.prototype.name = "我是原型中的名字";
        var mc = new MyClass();
        console.log(mc.__proto__.hasOwnProperty("hasOwnProperty"));       //false
        console.log(mc.__proto__.__proto__);    //  object
        console.log(mc.__proto__.__proto__.hasOwnProperty("hasOwnProperty"));   //true
        console.log(mc.__proto__.__proto__.__proto__);      //null
				console.log(mc.hello);      //undefined(没有这个属性)
```

