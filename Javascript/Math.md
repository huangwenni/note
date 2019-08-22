- [Math](#math)
	- [abs、ceil、floor、round、random](#abs、ceil、floor、round、random)
		- [Math.abs](#math.abs)
		- [Math.ceil](#math.ceil)
		- [Math.floor](#Math.floor)
		- [Math.round](#Math.round)
		- [Math.random](#Math.random)
	- [max、min、pow、sqrt](#max、min、pow、sqrt)

### Math

Math和其他对象不同，它不是一个构造函数，它属于一个工具类，不用创建对象，里面封装了数学运算相关的属性和方法。比如Math.PI表示圆周率。

#### abs、ceil、floor、round、random

**Math.abs()**

可以用来计算一个数的绝对值。

**Math.ceil()**

可以对一个数进行向上取整，小数位只要有值就自动进一。

**Math.floor()**

可以对一个数进行向下取整,小数部分会被舍掉。

**Math.round()**

可以对一个数进行四舍五入取整。

**Math.random()**

可以用来生成一个0-1之间的随机数。

生成0-x之间的随机数：

Math.round(Math.random() * x)

生成一个x-y之间的随机数：

Math.round(Math.random() * (y-x)) + x

```
        console.log(Math.abs(-5));      //5
        console.log(Math.ceil(1.4));        //2
        console.log(Math.floor(1.99));      //1
        console.log(Math.round(1.4));       //1
        for (var i=0;i<100;i++) {
            //console.log(Math.round(Math.random()*10));        //生成一个0-10之间的随机数
            console.log(Math.round(Math.random() * 9) + 1);     //生成一个1-10之间的随机数
        }
```

### max、min、pow(x,y)、sqrt

**Math.max**

可以获取多个数中的最大值。

**Math.min**

可以获取多个数中的最小值。

**pow**

返回x的y次幂。

**sqrt**

用于对一个数进行开方运算。

```
        var max = Math.max(10,20,30);
        var min = Math.min(10,20,30);
        console.log(max);       //30
        console.log(min);       //10

        console.log(Math.pow(2,2));     //4
        console.log(Math.sqrt(4));      //2
```