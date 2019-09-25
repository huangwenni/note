- [jQuery事件](#jquery事件)
	- [jQuery事件绑定和事件移除](#jquery事件绑定和事件移除)
		- [事件绑定](#事件绑定)
		- [事件移除](#事件移除)
	- [事件冒泡](#事件冒泡)
		-  [return false阻止事件冒泡](#return-false阻止事件冒泡)
		-  [event.stopPropagation阻止事件冒泡](#eventstoppropagation阻止事件冒泡)
	- [默认行为](#默认行为) 
		- [return false阻止默认行为](#return-false阻止默认行为)
		- [event.preventDefault阻止默认行为](#eventpreventdefault阻止默认行为)
	- [jQuery事件自动触发](#jquery事件自动触发)
	- [jQuery自定义事件](#jquery自定义事件)
	- [jQuery事件命名空间](#jquery事件命名空间)
		- [ jQuery事件命名空间的事件冒泡](#jquery事件命名空间的事件冒泡)
	- [jQuery事件委托](#jquery事件委托)
	- [jQuery移入移出事件](#jquery移入移出事件)
		- [TAB选项卡练习](#tab选项卡练习)
	
### jQuery事件

#### jQuery事件绑定和事件移除

##### 事件绑定

- eventName(fn)
	- 编码效率略高。
	- 部分事件jQuery没有实现，所以不能添加。
- on(eventName,fn)
	- 编码效率略低。
	- 所有js事件都可以添加。
- 注意点
	- 两个方法都可以添加多个相同或者不同类型的事件，不会覆盖。

```
            $('button').click(function () {
                alert('123');
            });
            $('button').click(function () {
                alert('maomao')
            });
            $('button').mouseleave(function () {
                alert('xiaomao');
            });
            $('button').mouseenter(function () {
                alert('aimaomao');
            });
```

```
            $('button').on('click1',function () {
                alert('456');
            });
            $('button').on('click2,fu'nction () {
                alert('maomao');
            });
            $('button').on('click3',function () {
                alert('xiaomao');
            });
            $('button').on('click4',function () {
                alert('aimaomao');
            });
```

##### 事件移除

- off()
	- 如果不传递参数，会移除所有的事件。
	- 如果传递一个参数，会移除所有指定类型的事件。
	- 如果传递两个参数，会移除所有指定类型的指定事件。

```
            function test1(){
                alert('123');
            }
            function test2(){
                alert('maomao');
            }
						
            $('button').click(test1);
            $('button').click(test2);

            //$('button').off();
            //$('button').off('click');
            $('button').off('click',test1);
```

#### 事件冒泡

body中的代码（以下都一样）：

```
<div class="father">
    <div class="son"></div>
</div>
```

##### return false阻止事件冒泡

```
            $('.son').click(function () {
                alert('son');
                return false;
            });
						
            $('.father').click(function () {
                alert('father');
            });
```

##### event.stopPropagation阻止事件冒泡

```
            $('.son').click(function (event) {
                alert('son');
                event.stopPropagation();
            });
						
            $('.father').click(function () {
                alert('father');
            });
```

#### 默认行为

body中的代码（以下都一样）：

```
<a href="http://www.baidu.com">我是百度</a>
<form action="http://www.taobao.com">
    <input type="text"/>
    <input type="submit"/>
</form>
```

##### return false阻止默认行为

```
            $('a').click(function () {
                alert('弹出注册框');
                return false;
            })
```

##### event.preventDefault阻止默认行为

```
            $('a').click(function (event) {
                alert('弹出注册框');
                event.preventDefault();
            })
```

#### jQuery事件自动触发

- trigger
	- 用trigger自动触发事件，会触发事件冒泡。
	- 会触发默认行为。
- triggerHandler
	- 用triggerHandler自动触发事件，不会触发事件冒泡。
	- 不会触发默认行为。

body中的代码（以下都一样）：

```
<div class="father">
    <div class="son"></div>
</div>
<a href="http://www.baidu.com"><span>注册</span></a>
<form action="http://www.taobao.com">
    <input type="text"/>
    <input type="submit"/>
</form>
```

自动触发事件：

```
            $('.father').trigger('click');
            $('.father').triggerHandler('click');
```

冒泡行为：

```
            //会触发事件冒泡
            $('.son').trigger('click');
```

```
            //不会触发事件冒泡
            $('.son').triggerHandler('click');
```

默认行为：

```
            $("input[type = 'submit']").click(function () {
               alert('123');
            });
            //会触发默认行为
            $("input[type = 'submit']").trigger('click');
```

```
            $("input[type = 'submit']").click(function () {
               alert('123');
            });
            //不会触发默认行为	
            $("input[type = 'submit']").triggerHandler('click');
```


a链接有个问题，不论是trigger还是triggerHandler都不会触发默认行为，除非是在a链接里加上`<span></span>`标签，用span来触发。

```
            $("a").click(function () {
                alert('a');
            });
            //不会触发默认行为	
            //$("a").triggerHandler("click");
            //不会触发默认行为	
            //$("a").trigger("click");
```

```
            $("span").click(function () {
                alert('a');
            });
            //会触发默认行为
            //$("span").trigger("click");				
            //不会触发默认行为	
            //$("span").triggerHandler("click");
```

#### jQuery自定义事件

- 事件必须是通过on绑定的。
- 事件必须通过trigger来触发。

```
            $(".son").on('myClick',function () {
                alert("son");
            });
            //触发事件				
            $(".son").trigger("myClick");
```

```
            $(".son").on('myClick',function () {
                alert("son");
            });
            //触发事件	
            $(".son").triggerHandler("myClick");
```

#### jQuery事件命名空间

- 事件是通过on来绑定的。
- 通过trigger触发事件。

```
            $(".son").on("click.zs",function () {
                alert("click1");
            });
            $(".son").on("click.ls",function () {
                alert("click2");
            });		
            //$(".son").trigger("click.zs");
            $(".son").trigger("click.ls");
```

##### jQuery事件命名空间的事件冒泡

- 利用trigger触发子元素带命名空间的事件，那么父元素带相同命名空间的事件也会被触发，而父元素没有命名空间的事件不会被触发。
- 利用trigger触发子元素不带命名空间的事件，那么子元素所有相同类型的事件和父元素所有相同类型的事件都会被触发。

```
            $(".father").on("click.ls",function () {
                alert("father click1");
            });
            $(".father").on("click",function () {
                alert("father click2");
            });
            $(".son").on("click.ls",function () {
                alert("son click1");
            });
						
            $(".son").trigger("click.ls")
            //触发son click1和father click1
```

```
            $(".father").on("click.ls",function () {
                alert("father click1");
            });
            $(".father").on("click",function () {
                alert("father click2");
            });
            $(".son").on("click.ls",function () {
                alert("son click1");
            });

            $(".son").trigger("click")
            //触发son click1、father click1、father click2
```

#### jQuery事件委托

- 找一个在入口函数执行之前就有的元素，来监听你动态添加元素的某些事件。

body中的代码：

```
<ul>
    <li>我是第1个li</li>
    <li>我是第2个li</li>
    <li>我是第3个li</li>
</ul>
<button>新增一个li</button>
```

在以下代码中，新增的li不会在控制台输出（新增的li不会绑定点击事件）。

```
            $("button").click(function () {
                $("ul").append("<li>我是新增的li</li>");
            });
						
            $("ul>li").click(function () {
                console.log($(this).html());
            });
```

解决方式：使用事件委托

```
            $("ul>li").click(function () {
                console.log($(this).html());
            });

            $("ul").delegate("li","click",function () {
                console.log($(this).html());
            })；
```

#### jQuery移入移出事件

- mouseover/mouseout事件，子元素被移入移出也会触发父元素的事件。
- mouseenter/mouseleave事件，子元素被移入移出不会触发父元素的事件（推荐使用）。
- hover事件，用mouseover/mouseout事件实现，子元素被移入移出不会触发父元素的事件。

```
            $(".father").mousemove(function () {
                console.log("father被移入了");
            });
            $(".father").mouseout(function () {
                console.log("father被移出了");
            });
```

```
            $(".father").mouseenter(function () {
                console.log("father被移入了");
            });
            $(".father").mouseleave(function () {
                console.log("father被移出了");
            });
```

```
            $(".father").hover(function () {
                console.log("father被移入了")
            },function () {
                console.log("father被移出了");
            });
```

##### TAB选项卡练习

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <style>
        *{
            margin: 0;
            padding: 0;
        }
        .box{
            width: 440px;
            height: 298px;
            border: 1px solid #000;
            margin: 50px auto;
        }
        .nav>li{
            list-style: none;
            width: 110px;
            height: 50px;
            background: orange;
            text-align: center;
            line-height: 50px;
            float: left;
        }
        .nav>.current{
            background-color: #cccccc;
        }
        .content>li{
            list-style: none;
            display: none;
        }
        .content>.show{
            display: block;
        }
    </style>
    <script src="js/jquery-1.12.4.js"></script>
    <script>
        $(function () {
            /*
            注意：以下方法会使得鼠标移出后没有图片保留
            //监听选项卡的移入事件
            $(".nav>li").mouseenter(function () {
                //修改被移入选项卡的背景颜色
                $(this).addClass("current");
								
                var index = $(this).index();
                //根据索引找到对应的图片
                var $li = $(".content>li").eq(index);
                //显示找到的图片
                $li.addClass("show");
            });
            //监听选项卡的移出事件
            $(".nav>li").mouseleave(function () {
                //修改被移入选项卡的背景颜色
                $(this).removeClass("current");
                var index = $(this).index();
                var $li = $(".content>li").eq(index);
                $li.removeClass("show");
            });
            */
						
            //应使用以下写法
            $(".nav>li").mouseenter(function () {
                $(this).addClass("current");
                //还原其他兄弟选项卡的背景颜色
                $(this).siblings().removeClass("current");
                var index = $(this).index();
                var $li = $(".content>li").eq(index);
                $li.siblings().removeClass("show");
                $li.addClass("show");
            });
        });
    </script>
</head>
<body>
<div class="box">
    <ul class="nav">
        <li class="current">H5C3</li>
        <li>jQuery</li>
        <li>C语言</li>
        <li>Go语言</li>
    </ul>
    <ul class="content">
        <li class="show"><img src="images/2.jpg" alt=""></li>
        <li><img src="images/3.jpg" alt=""></li>
        <li><img src="images/4.jpg" alt=""></li>
        <li><img src="images/5.jpg" alt=""></li>
    </ul>
</div>
</body>
</html>
```








