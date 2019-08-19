- [jQuery方法与原生js方法](#jquery方法与原生js方法)
	- [静态方法和实例方法](#静态方法和实例方法)
	- [遍历](#遍历)
		- [原生js的forEach方法](#原生js的foreach方法)
		- [jQuery的each方法](#jquery的each方法)
		- [原生js的map方法](#原生js的map方法)
		- [jQuery的map方法](#jquery的map方法)
		- [jQuery的each静态方法和map静态方法的区别](#jquery的each静态方法和map静态方法的区别)
- [jQuery中的其他静态方法](#jquery中的其他静态方法)
	- [trim方法](#trim方法)
	- [isWindow方法](#iswindow方法)
	- [isArray方法](#isarray方法])
	- [isFunction方法](#isfunction方法)
	- [holdReady方法](#holdready方法)
- [jQuery属性操作](#jquery属性操作)
	- [属性](#属性)
		- [attr方法](#attr方法)
		- [removeAttr方法](#removeattr方法)
		- [prop方法](#prop方法)
		- [removeProp方法](#removeprop方法)
		- [选择prop还是arr？](#选择prop还是arr？)
	- [CSS](#css)
	- [HTML代码/文本/值](#html代码文本值)
- [jQuery的CSS操作](#jquery的css操作) 
	- [CSS](#css)
	- [位置](#位置)
	- [尺寸](#尺寸)

### jQuery方法与原生js方法

#### 静态方法和实例方法

静态方法通过类名调用；实例方法通过类的实例调用。

```
        //定义一个类
        function AClass() {}
        //给类添加一个静态方法
        AClass.staticMethod = function () {
            alert('staticMethod');
        };

        //静态方法通过类名调用
        AClass.staticMethod();

        //给类添加一个实例方法
        AClass.prototype.instanceMethod = function () {
            alert('instanceMethod');
        };

        //实例方法通过类的实例调用
        //创建一个实例（创建一个对象）
        var a = new AClass();
        a.instanceMethod();
```

#### 遍历

##### 原生js的forEach方法

- 第一个参数：遍历到的元素。
- 第二个参数：当前遍历到的索引。
- 注意
	- 原生的forEach方法只能遍历数组，不能遍历伪数组。

```
        var arr = [1,3,5,7,9];
        var obj = {0:1,1:3,2:5,3:7,4:9,length:5};
				
        arr.forEach(function (value,index) {
            console.log(index,value);
        });

        //伪数组，会报错
        obj.forEach(function (value,index) {
            console.log(index,value);
        })
```

##### jQuery的each方法

- 第一个参数：当前遍历到的索引。
- 第二个参数：遍历到的元素。
- 注意
	- jQuery的each方法是可以遍历伪数组的。

```
        var arr = [1,3,5,7,9];
        var obj = {0:1,1:3,2:5,3:7,4:9,length:5};
				
		//以下都不会报错

        $.each(arr,function (index,value) {
            console.log(index,value);
        });

        */

        $.each(obj,function (index,value) {
            console.log(index,value);
        });
```

##### 原生js的map方法

- 第一个参数：当前遍历到的元素。
- 第二个参数：当前遍历到的索引。
- 第三个参数：当前被遍历的数组。
- 注意
	- 和原生的forEach一样，不能遍历伪数组。

```
        var arr = [1,3,5,7,9];
        var obj = {0:1,1:3,2:5,3:7,4:9,length:5};
				
        arr.map(function (value,index,array) {
            console.log(index,value,array);
        });

        //伪数组会报错
        obj.map(function (value,index,array) {
            console.log(index,value,array);
        });
```

##### jQuery的map方法

- 第一个参数：要遍历的数组。
- 第二个参数：每遍历一个元素之后执行的回调函数。
	- 回调函数的参数
		- 第一个参数:遍历到的元素。
		- 第二个参数:遍历到的索引。
- 和jQuery中的each静态方法一样，map静态方法也可以遍历伪数组。

```
        var arr = [1,3,5,7,9];
        var obj = {0:1,1:3,2:5,3:7,4:9,length:5};
		
		//以下都不会报错

        $.map(arr,function (value,index) {
            console.log(index,value);
        });

        $.map(obj,function (value,index) {
            console.log(index,value);
        });
```

##### jQuery的each静态方法和map静态方法的区别

- 区别一
	- each静态方法默认的返回值：遍历谁就返回谁。
	- map静态方法默认的返回值：一个空数组。
	
```
        var res = $.map(obj,function (value,index) {
            console.log(index,value);
        });

        var  res2 = $.each(obj,function (index,value) {
            console.log(index,value);
        });

        console.log(res);
        //[]
        console.log(res2);
        //{0: 1, 1: 3, 2: 5, 3: 7, 4: 9, length: 5}
```
	
- 区别二
	- each静态方法不支持在回调函数中对遍历的数组进行处理。
	- map静态方法可以在回调函数中通过return对遍历的数组进行处理，然后生成一个新的数组返回。

```
		//可以正常执行
        var res = $.map(obj,function (value,index) {
            console.log(index,value);
            return value += index;
        });
		
		//each方法会报错
        var  res2 = $.each(obj,function (index,value) {
            console.log(index,value);
            return value += index;
        });

        console.log(res);
        console.log(res2);
```

#### jQuery中的其他静态方法

##### trim方法

- $.trim()
- 作用：去除字符串两端的空格。
- 参数：需要去除空格的字符串。
- 返回值：去除空格之后的字符串。

```
        var str = ' maomao ';
        var res = $.trim(str);
        console.log('---'+str+'---');
        console.log('---'+res+'---');
```

##### isWindow方法

- $.isWindow()
- 作用：判断传入的对象是否是window对象。
- 返回值：true/false。

```
        //真数组
        var arr = [1,3,5,7,9];
        //伪数组
        var arrlike = {0:1,1:3,2:5,3:7,4:9,length:5};
        //对象
        var obj = {'name':'maomao',age:'22'};
        //函数
        var fn = function () {};
        //window对象
        var w = window;
				
        var res = $.isWindow(w);
        console.log(res);
        //true
```

##### isArray方法

- $.isArray()
- 作用：判断传入的对象是否是真数组。
- 返回值：true/false。

```
        var arr = [1,3,5,7,9];

        var res = $.isArray(arr);
        console.log(res);
        //true
```

##### isFunction方法

- $.isFunction()
- 作用：判断传入的对象是否是一个函数。
- 返回值：true/false。
- 注意点：jQuery本质上是一个函数。

```
        var fn = function () {};

        var res = $.isFunction(fn);
        console.log(res);
        //true

        var res = $.isFunction(jQuery);
        console.log(res);
        //true

        //立即执行函数
        (function (window,undefined) {
        })(window);
```

##### holdReady方法

- $.holdReady()
- 作用：暂停、恢复ready事件。

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <script src="js/jquery-1.12.4.js"></script>
    <script>
        $.holdReady(true); 			//暂停ready执行
        $(document).ready(function () {
            alert('ready');
        });
    </script>
</head>

<body>
<button>恢复ready事件</button>
<script>
    var btn = document.getElementsByTagName('button')[0];
    btn.onclick = function () {
        $.holdReady(false);    		 //恢复ready事件
    }
</script>
</body>
</html>
```

### jQuery的属性操作

#### 属性

body中的代码（以下例子都是如此）：

```
<span class="span1" name="it666"></span>
<span class="span2" name="maomao"></span>
```

##### attr方法

- attr(name|pro|key.val|fn)
- 作用：获取或者设置属性节点的值。
- 可以传递一个参数，也可以传递两个参数。
- 如果传递一个参数，发表获取属性节点的值。
- 如果传递两个参数，代表设置属性节点的值。
- 注意点
	- 如果是获取：无论找到多少个元素，都只会返回第一个元素指定的属性节点的值。
	- 如果是设置：找到多少个元素就会设置多少个元素。
	- 如果是设置：如果设置的属性节点不存在，那么系统会自动新增。


```
                console.log($('span').attr('class'));
                //span1

                $('span').attr('class','box');
                //两个span标签的class都会变成box

                $('span').attr('abc','123');
								//属性节点不存在，系统会自动新增
```

##### removeAttr方法

- removeAttr(name)
- 作用删除属性节点。
- 注意点
	- 会删除所有找到元素指定的属性节点。
	- 可同时设置多个。

```
                $('span').removeAttr('class');
                $('span').removeAttr('class name');
```

##### prop方法

- 特点和attr方法一致。
- 注意点
	- prop方法不仅能够操作属性，还能操作属性节点。

```
                //操作属性
                console.log($('span').prop('class'));
                $('span').prop('class','box');

                //操作属性节点
                $('span').eq(0).prop('demo','it666');
                $('span').eq(1).prop('demo','maomao');
                console.log($('span').prop('demo'));    //it666
```

##### removeProp方法

- 特点和removeAttr方法一致。

```
                $('span').removeProp('demo');
```

##### 选择prop还是arr？

官方推荐在操作属性节点时，具有true和false两个属性的属性节点，如`checked`、
`selected`或者`disabled` ，使用prop()。其他使用 arr()。

```
<input type="checkbox" checked>
```
```
                //选中情况
								
                console.log($('input').prop('checked'));
                //true

                console.log($('input').attr('checked'));
                //checked
```
```
<input type="checkbox">
```
```
                //没选中情况
								
                console.log($('input').prop('checked'));
                //false

                console.log($('input').attr('checked'));
                //undefined
```

#### CSS类

- **addClass(class|fn)**
	- 作用：添加一个类。
	- 如果要添加多个，多个类名之间用空格隔开即可。
- **removeClass([class|fn])**
	- 作用：删除一个类。
	- 如果要添加多个，多个类名之间用空格隔开即可。
- **toggleClass(class|fn[,sw])**
	- 作用：切换类。
	- 有就删除，没有就添加。

```
                var btns = document.getElementsByTagName('button');
                btns[0].onclick = function () {
                    $('div').addClass('class1 class2');
                };
                btns[1].onclick = function () {
                    $('div').removeClass('class1 class2');
                };
                btns[2].onclick = function () {
                    $('div').toggle('class1 class2');
                };
```

#### HTML代码/文本/值

- **html([val|fn])**
	- 和原生JS中的innerHtml一模一样。
- **text([val|fn])**
	- 和原生JS中的innerText一模一样。

```
            var btns = document.getElementsByTagName('button');
            btns[0].onclick = function () {
                $('div').html('<p>我是段落<span>我是span</span></p>');
            };
            btns[1].onclick = function () {
                console.log($('div').html());
            };
            btns[2].onclick = function () {
                $('div').text('<p>我是段落<span>我是span</span></p>');
            };
            btns[3].onclick = function () {
                console.log($('div').text());
            };
            btns[4].onclick = function () {
                $('input').val('请输入内容');
            };
            btns[5].onclick = function () {
                console.log($('input').val());
            };
```

### jQuery的CSS操作

#### CSS

```
            //1.逐个设置
                $('div').css('width','100px');
                $('div').css('height','100px');
                $('div').css('background','red');
								
            //2.链式设置
            //注意点：链式操作如果大于3步，建议分开
                $('div').css('width','100px').css('height','100px').css('background','blue');
								
            //3.批量设置（企业开发推荐使用）
                $('div').css({
                    width:'100px',
                    height:'100px',
                    background:'red'
                })
								
            //4.获取CSS样式值
            console.log($('div').css('width'));
```

#### 位置

- offse([coordinates])
	- 作用：获取和设置元素距离窗口的偏移位。
-  position()
	- 作用：获取元素距离定位元素的偏移位。
	- 注意点
		- position方法只能获取，不能设置。
		- 想要设置可以使用css方法。

body标签中的代码：

```
<body>
<div class="father">
    <div class="son"></div>
</div>
<button>获取</button>
<button>设置</button>
</body>
```

script标签中的代码：

```
        <script>
            $(function () {
                var btns = document.getElementsByTagName('button');
								
                //监听获取
                btns[0].onclick = function () {
                    console.log($('.son').offset().left);
                    console.log($('.son').position().left);
                }
								
                //监听设置
                btns[1].onclick = function () {
                    $('.son').offset({
                        left:10
                    });
                    $('.son').css({
                        left:'10px'
                    })；
                }
            });
        </script>
```

- scrollTop()
	- 获取和设置滚动的偏移位。
	- 注意点
		- 为了保证浏览器的兼容， 获取网页滚动的偏移位需要按照如下写法：
		
		```
		console.log($('html').scrollTop());
		```
		
		- 为了保证浏览器的兼容， 设置网页滚动的偏移位需要按照如下写法：
		
		```
		$('html,body').scrollTop(300);
		```

```
    <script>
        $(function () {
            var btns = document.getElementsByTagName('button');
            //监听获取
            btns[0].onclick = function () {
                //获取滚动的偏移位
                console.log($('.scroll').scrollTop());
                //获取网页滚动的偏移位
                console.log($('html').scrollTop());
            };
            btns[1].onclick = function () {
                //设置滚动的偏移位
                $('.scroll').scrollTop(300);
                //设置网页滚动偏移位
                // 注意点：为了保证浏览器的兼容， 设置网页滚动的偏移位需要按照如下写法
                $('html,body').scrollTop(300);
            };
         });
    </script>
```


#### 尺寸

```
  var btns = document.getElementsByTagName('button');
                //监听获取
                btns[0].onclick = function () {
                    console.log($('.father').width());
                }
                //监听设置
                btns[1].onclick = function () {
                    $('.father').width('500px');
                }
            });
```



























