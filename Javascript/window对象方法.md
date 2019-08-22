- [window对象方法](#window对象方法)
	- [setInterval()](#setinterval)
	- [clearInterval()](#clearinterval)
	- [定时器练习](#定时器练习)
	- [setTimeout()](#settimeout)
	- [clearTimeout()](#cleartimeout)
	- [定时器练习2](#定时器练习2)
	- [定时器练习3](#定时器练习3)

### window对象方法

#### setInterval()

定时调用，可以将一个函数，每隔一段时间执行一次。

**参数**

1、回调函数，该函数会每隔一段时间被调用一次。

2、每次调用间隔的时间，单位是毫秒。

**返回值**

返回一个Number类型的数据，这个数字用来作为定时器的唯一标识。

#### clearInterval()

可以用来关闭一个定时器，方法中需要一个定时器的标识作为参数，这样将关闭标识对应的定时器。

clearInterval()可以接收任意参数，如果参数是一个有效的定时器的标识，则停止对应的定时器，如果参数不是一个有效的标识，则什么也不做。

#### 定时器练习

```
<h1 id="count"></h1>
```

每一秒增加一个数字，直到200：

```
        window.onload = function () {
            var count = document.getElementById("count");
            //定时调用
            var num = 1;
            var timer = setInterval(function () {
                count.innerText = num++;
                if (num ==200){
                    //关闭定时器
                    clearInterval(timer);
                }
            },1000);
            //返回一个Number类型的值
            console.log(timer);
        };
```

图片自动切换，点击按钮开始停止：

```
<body>
<img id="img1" src="1.jpg"/>
<br /><br />
<button id="btn01">开始</button>
<button id="btn02">停止</button>
</body>
```
```
    <script>
        window.onload = function () {
          var img1 = document.getElementById("img1");
          var imgArr = ["1.jpg","2.jpg","3.jpg","4.jpg","5.jpg"];
          var index = 0;
          var timer;

          var btn01 = document.getElementById("btn01");
          btn01.onclick = function(){
                /*
                每点击一次按钮，就会开启一个定时器，
                点击多次就会开启多个定时器，这就导致图片的切换速度过快，
          	    并且我们只能关闭最后一次开启的定时器
          	    因此，在开启下一个定时器之前，要把上一个关闭
          	    */
            clearInterval(timer) ;
            timer = setInterval(function () {
                  index++;
                  //判断索引是否超过最大索引
                  /*
                  if (index>=imgArr.length){
                      index = 0;
                  }
                  */
                  //与上面的效果一样
                  index %= imgArr.length;
                  img1.src = imgArr[index];
              },1000);
          };
          var btn02 = document.getElementById("btn02");
          btn02.onclick = function () {
              clearInterval(timer);
          };
        };
    </script>
```

#### setTimeout()

延时调用一个函数不马上执行，而是隔一段时间以后在执行，而且只会执行一次。

延时调用和定时调用的区别，定时调用会执行多次，而延时调用只会执行一次。

延时调用和定时调用实际上是可以互相代替的，在开发中可以根据自己需要去选择。

#### clearTimeout()

```
        var num = 1;
        var timer = setTimeout(function () {
            console.log(num++);
        },3000);
        clearTimeout(timer);
```

#### 定时器练习2

点击按钮div向右移动。

```
<button id="btn01">点击按钮以后box1向右移动</button>
<br /><br />
<div id="box1"></div>
<div style="width: 0; height: 1000px; border-left:1px black solid; position: absolute; left: 800px;top:0;"></div>
```
```
        window.onload = function () {
            var box1 = document.getElementById("box1");
            var btn01 = document.getElementById("btn01");
            var timer;
            btn01.onclick = function () {
                clearInterval(timer);
                    timer = setInterval(function () {
                    var oldValue = parseInt(getStyle(box1,"left"));
                    var newValue = oldValue + 11;
                    if (newValue>800){
                        newValue = 800;
                    }
                    box1.style.left = newValue + "px";
                    if (newValue === 800){
                        clearInterval(timer);
                    }
                },30);
            };
            function getStyle(obj,name) {
                if (window.getComputedStyle) {
                    return getComputedStyle(obj, null)[name];
                } else {
                    return obj.currentStyle[name];
                }
            }
       };
</script>
```

#### 定时器练习3

点击按钮左右移动。
```
<button id="btn01">点击按钮以后box1向右移动</button>
<button id = "btn02">点击按钮后box2向左移动</button>
<br /><br />
<div id="box1"></div>
<div style="width: 0; height: 1000px; border-left:1px black solid; position: absolute; left: 800px;top:0;"></div>
```
```
    <script>
        window.onload = function () {
            var box1 = document.getElementById("box1");
            var btn01 = document.getElementById("btn01");
            var brn02 = document.getElementById("btn02");
            btn01.onclick = function(){
                move(box1,800,10);
            };
            btn02.onclick = function(){
                move(box1,0,10);
            };
        };
            var timer;
                function move(obj,target,speed) {
                    clearInterval(timer);
                    var current = parseInt(getStyle(obj,"left"));
                    if (current>target) {
                        speed = -speed;
                    }
                    timer = setInterval(function () {
                        var oldValue = parseInt(getStyle(obj,"left"));
                        var newValue = oldValue + speed;
                        //当向左移动时，值越来越小，判断是否小于target
                        if ((speed < 0 && newValue<target) || (speed > 0 && newValue>target)){
                            newValue = target;
                        }
                        obj.style.left = newValue + "px";
                        if (newValue === target){
                            clearInterval(timer);
                        }
                    },30);
                }
            function getStyle(obj,name) {
                if (window.getComputedStyle) {
                    return getComputedStyle(obj, null)[name];
                } else {
                    return obj.currentStyle[name];
                }
            }
    </script>
```

#### 定时器练习3

上面的方法会存在问题：添加另一个动画会影响到前一个动画的执行。

**最终解决和优化方式**

```
<button id="btn01">点击按钮以后box1向右移动</button>
<button id="btn02">点击按钮以后box1向左移动</button>
<button id="btn03">点击按钮以后box2向右移动</button>
<button id="btn04">测试按钮</button>
<br /><br />
<div id="box1"></div>
<div id="box2"></div>
<div style="width: 0; height: 1000px; border-left:1px black solid; position: absolute; left: 800px;top:0;"></div>
```
```
    <script type="text/javascript">
        window.onload = function () {
            var box1 = document.getElementById("box1");
            var btn01 = document.getElementById("btn01");
            var brn02 = document.getElementById("btn02");
            btn01.onclick = function(){
                move(box1,"left",800,20);
            };
            btn02.onclick = function(){
                move(box1,"left",0,10);
            };

            var btn03 = document.getElementById("btn03");
            btn03.onclick = function () {
                move(box2,"left",800,10);
            };
            var btn04 = document.getElementById("btn04");
            btn04.onclick = function () {
                //move(box2,"width",800,10);
                move(box2,"width",800,10,function () {
                    move(box2,"height",400,10,function () {
                        
                    })
                });
            };
        };

        //var timer;        //不能用，存在隐患
        /*
        * 参数：
        * obj：要执行动画的对象
        * attr：要执行动画的样式
        * target：执行动画的目标位置
        * speed：移动的速度
        * callback：回调函数，这个函数将会在动画执行完毕以后执行
        *
        * */
        
        function move(obj,attr,target,speed,callback) {
            clearInterval(obj.timer);
            var current = parseInt(getStyle(obj,attr));
            if (current>target) {
                speed = -speed;
            }
            //向执行动画的对象中添加一个timer属性，用来保存它自己的定时器标识
            //保存自己的定时器，一个动画的执行不会影响到另一个
            obj.timer = setInterval(function () {
                var oldValue = parseInt(getStyle(obj,attr));
                var newValue = oldValue + speed;
                //当向左移动时，值越来越小，判断是否小于target
                if ((speed < 0 && newValue<target) || (speed > 0 && newValue>target)){
                    newValue = target;
                }
                obj.style[attr] = newValue + "px";
                if (newValue === target){
                    clearInterval(obj.timer);
                    //如果有才调用，如果没有就不调用
                    callback && callback();
                }
            },30);
        }
        function getStyle(obj,name) {
            if (window.getComputedStyle) {
                return getComputedStyle(obj, null)[name];
            } else {
                return obj.currentStyle[name];
            }
        }
    </script>
```

