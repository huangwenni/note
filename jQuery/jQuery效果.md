- [jQuery效果](#jquery效果)
	- [ jQuery显示和隐藏动画](#jquery显示和隐藏动画)
		- [对联广告练习](#对联广告练习)
	- [jQuery滑动](#jquery滑动)
	- [jQuery淡入淡出动画](#jquery淡入淡出动画)
		- [弹窗广告练习](#弹窗广告练习)
	- [jQuery自定义动画](#jquery自定义动画)
		- [animate方法](#animate方法)
	- [jQuery的stop和delay方法](#jquery的stop和delay方法)
		- [stop](#stop)
		- [delay](#delay)
	- [图标特效练习](#图标特效练习)

### jQuery效果

#### jQuery显示和隐藏动画

- show
	- 缓慢显示。
- hide
	- 缓慢隐藏。
- toggle
	- 缓慢切换。

body标签中的代码：

```
<button>显示</button>
<button>隐藏</button>
<button>切换</button>
<div></div>
```

script标签中的代码：

```
            $("button").eq(0).click(function () {
                //$("div").css("display","block");
                $("div").show(1000,function () {
                });
            });
            $("button").eq(1).click(function () {
                //$("div").css("display","none");
                $("div").hide(1000,function () {
                });
            });
            $("button").eq(2).click(function () {
                $("div").toggle(1000,function () {
                });
            });
```

##### 对联广告练习

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
        .left{
            float: left;
            position: fixed;
            left: 0;
            top: 200px;
        }
        .right{
            float: right;
            position: fixed;
            right: 0;
            top: 200px;
        }
        img{
            display: none;
        }
    </style>
    <script src="js/jquery-1.12.4.js"></script>
    <script>
        $(function () {
            $(window).scroll(function () {
                //获取网页滚动偏移位
                var offset = $("html,body").scrollTop();
                //判断网页是否滚动到了指定位置
                if (offset>=100){
                    //显示广告
                    $("img").show(1000);
                }else {
                    $("img").hide(1000);
                }
            });
        });
    </script>
</head>
<body>
<img src="images/1.jpg" class="left"/>
<img src="images/1.jpg" class="right"/>
</body>
</html>
```

#### jQuery滑动

- slideDown
	- 向下滑动
- slideUp
	- 向上滑动
- slideToggle
	- 向下向上滑动切换


**展开和收起动画**

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
        div{
            width: 100px;
            height: 300px;
            background: red;
            display: none;
        }
    </style>
    <script src="js/jquery-1.12.4.js"></script>
    <script>
        $(function () {
            $("button").eq(0).click(function () {
                $("div").slideDown(1000,function () {
                })
            });
            $("button").eq(1).click(function () {
                $("div").slideUp(1000,function () {
                })
            });
            $("button").eq(2).click(function () {
                $("div").slideToggle(1000,function () {
                })
            });
        });
    </script>
</head>
<body>
<button>展开</button>
<button>收起</button>
<button>切换</button>
<div></div>
</body>
</html>
```

#### jQuery淡入淡出动画

- fadeIn
	- 淡入。
- fadeOut
	- 淡出。
- fadeToggle
	- 淡入淡出切换。
- fadeTo
	- 淡入到，可以指定淡入到什么程度。

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
        div{
            width: 300px;
            height: 300px;
            background: red;
            display: none;
        }
    </style>
    <script src="js/jquery-1.12.4.js"></script>
    <script>
        $(function () {
            //淡入
            $("button").eq(0).click(function () {
                $("div").fadeIn(1000,function () {
                });
            });
            //淡出
            $("button").eq(1).click(function () {
                $("div").fadeOut(1000,function () {
                });
            });
            //切换
            $("button").eq(2).click(function () {
                $("div").fadeToggle(1000,function () {
                });
            });
            //淡入到：可以指定淡入到什么程度，这里设置的是0.5
            $("button").eq(3).click(function () {
                $("div").fadeTo(1000,0.5,function () {
                });
            });
        });
    </script>
</head>
<body>
<button>淡入</button>
<button>淡出</button>
<button>切换</button>
<button>淡入到</button>
<div></div>
</body>
</html>
```

##### 弹窗广告练习

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
        .ad{
            position: fixed;
            right: 0;
            bottom: 0;
            display: none;
        }
        .ad>span{
            display: inline-block;
            width: 30px;
            height: 30px;
            background: brown;
            position: absolute;
            top: 0;
            right: 0;
        }
    </style>
    <script src="js/jquery-1.12.4.js"></script>
    <script>
        $(function () {
            //监听span的点击事件
            $("span").click(function () {
                $(".ad").remove();
            });
            //执行广告动画
            //function中的代码在动画执行完毕之后才会调用
            /*
            $(".ad").slideDown(1000,function () {
                $(".ad").fadeOut(1000,function () {
                    $(".ad").fadeIn(1000);
                });
            });
            */
            $(".ad").stop().slideDown(1000).fadeOut(1000).fadeIn(1000);
        });
    </script>
</head>
<body>
<div class="ad">
    <img src="images/2.jpg" alt=""/>
    <span></span>
</div>
</body>
</html>
```

#### jQuery自定义动画

##### animate方法

- 第一个参数：接受一个对象，可以在对象中修改属性。
- 第二个参数：指定动画时长。
- 第三个参数：指定动画节奏(可写可不写)，默认是swing。
- 第四个参数：动画执行完毕之后的回调函数。

body标签中的代码：

```
<button>操作属性</button>
<button>累加属性</button>
<button>关键字</button>
<div class="one"></div>
<div class="two"></div>
```

script标签中的代码：

```
            $("button").eq(0).click(function () {
                $(".one").animate({
                    marginLeft:500
                },5000,function () {
                });
                $(".two").animate({
                    marginLeft:500
                },5000,"linear",function () {
                });
            });
```

可连接字符串：

```
            $("button").eq(1).click(function () {
                $(".one").animate({
                    width:"+=100"
                },1000,function () {
                });
            });
```

隐藏与切换：

```
            $("button").eq(2).click(function () {
                $(".one").animate({
                    //width:"hide"
                    width:"toggle"
                },1000,function () {
                });
            });
```

#### jQuery的stop和delay方法

body中的代码（以下都一样）：

```
<button>开始动画</button>
<button>停止动画</button>
<div class="one"></div>
<div class="two"></div>
```

**在jQuery的{}中可以同时修改多个属性，多个属性的动画也会同时执行。**

```
            $("button").eq(0).click(function () {
                $(".one").animate({
                    width:500,
                    height:500
                },1000);
            });
```

**如果不想同时执行，可以分开写。**

```
            $("button").eq(0).click(function () {
                $(".one").animate({
                    width:500
                },1000);

                $(".one").animate({
                    height:500
                },1000);
            });
```

**可以连写。**

```
            $("button").eq(0).click(function () {
                $(".one").animate({
                    width:500
                },1000).animate({
                    height:500
                },1000);
            });
```

##### stop

```
            $("button").eq(1).click(function () {
                //立即停止当前动画，继续执行后续的动画
                //$("div").stop();
                //$("div").stop(false);
                //$("div").stop(false,false);

                //立即停止当前和后续所有的动画
                //$("div").stop(true);
                //$("div").stop(true,false);

                //立即完成当前的，继续执行后续动画
                //$("div").stop(false,true);

                //立即完成当前的，并且停止后续所有的
                $("div").stop(true,true);
            });
```

##### delay

- delay
	- 用于告诉系统延迟时长。

```
            $("button").eq(0).click(function () {
                $(".one").animate({
                    width:500
                },1000).delay(2000).animate({
                    height:500
                },1000);
            });

                $(".one").animate({
                    width:500
                },1000);

                $(".one").animate({
                    height:500
                },1000);

                $(".one").animate({
                    width:100
                },1000);

                $(".one").animate({
                    height:100
                },1000);
```

#### 图标特效练习

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
        ul{
            list-style: none;
            width: 400px;
            height: 250px;
            border: 1px solid #000;
            margin: 100px auto;
        }
        ul>li{
            width: 100px;
            height: 50px;
            margin-top: 50px;
            text-align: center;
            float: left;
            overflow: hidden;
        }
        ul>li>span{
            display: inline-block;
            width: 24px;
            height: 24px;
            background:url("images/bg.png") no-repeat 0 0;
            position: relative;
        }
    </style>
    <script src="js/jquery-1.12.4.js"></script>
    <script>
        $(function () {
            $("li").each(function (index,ele) {
                //生成新的图片位置
                var $url = "url(\"iamges/bg.png\") no-repeat 0 "+(index * -24)+"px";
                //设置新的图片位置
                $(this).children("span").css("background",$url);
            });
            //监听li移入事件
            $("li").mouseenter(function () {
                //将图标往上移动
                $(this).children("span").animate({
                    top:-50
                },1000,function () {
                    //将图标往下移动
                    $(this).css("top","50px");
                    //将图片复位
                    $(this).animate({
                        top:0
                    },1000);
                });
            });
        });
    </script>
</head>
<body>
<ul>
    <li><span></span><p>百度</p></li>
    <li><span></span><p>百度</p></li>
    <li><span></span><p>百度</p></li>
    <li><span></span><p>百度</p></li>
    <li><span></span><p>百度</p></li>
    <li><span></span><p>百度</p></li>
    <li><span></span><p>百度</p></li>
</ul>
</body>
</html>
```





















 






