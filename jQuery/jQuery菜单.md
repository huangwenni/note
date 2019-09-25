- [jQuery菜单](jquery菜单)
	- [jQuery折叠菜单](#jquery折叠菜单)

### jQuery菜单

#### jQuery折叠菜单

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
        .nav{
            list-style: none;
            width: 300px;
            margin: 100px auto;
        }
        .nav>li{
            border: 1px solid #000;
            line-height: 35px;
            border-bottom: none;
            text-indent: 2em;
            position: relative;
        }
        .nav>li:last-child{
            border-bottom: 1px solid #000000;
            border-bottom-right-radius: 5px;
            border-bottom-left-radius: 5px;
        }
        .nav>li:first-child{
            border-top-right-radius: 10px;
            border-top-left-radius: 10px;
        }
        .nav>li>span{
            background:url("images/1.jpg") no-repeat center center;
            display: inline-block;
            width: 25px;
            height: 25px;
            position: absolute;
            right: 10px;
            top: 5px;
        }
        .sub{
            display: none;
        }
        .sub>li{
            list-style: none;
            background: mediumaquamarine;
            border-bottom: 1px solid white;
        }
        .sub>li:hover{
            background: brown;
        }
        .nav>.current>span{
            transform: rotate(90deg);
        }
    </style>
    <script src="js/jquery-1.12.4.js"></script>
    <script>
        $(function () {
            $(".nav>li").click(function () {
                var $sub = $(this).children(".sub");
                $sub.slideDown(1000);
                var otherSub = $(this).siblings().children(".sub");
                otherSub.slideUp(1000);
                //让被点击的一级菜单箭头旋转
                $(this).addClass("current");
                $(this).siblings().removeClass("current");
            });
        });
    </script>
</head>
<body>
<ul class="nav">
    <li class="current">一级菜单<span></span>
        <ul class="sub">
            <li>二级菜单</li>
            <li>二级菜单</li>
            <li>二级菜单</li>
            <li>二级菜单</li>
            <li>二级菜单</li>
        </ul>
    </li>
    <li>一级菜单<span></span>
        <ul class="sub">
            <li>二级菜单</li>
            <li>二级菜单</li>
            <li>二级菜单</li>
            <li>二级菜单</li>
            <li>二级菜单</li>
        </ul>
    </li>
    <li>一级菜单<span></span>
        <ul class="sub">
            <li>二级菜单</li>
            <li>二级菜单</li>
            <li>二级菜单</li>
            <li>二级菜单</li>
            <li>二级菜单</li>
        </ul>
    </li>
    <li>一级菜单<span></span>
        <ul class="sub">
            <li>二级菜单</li>
            <li>二级菜单</li>
            <li>二级菜单</li>
            <li>二级菜单</li>
            <li>二级菜单</li>
        </ul>
    </li>
    <li>一级菜单<span></span>
        <ul class="sub">
            <li>二级菜单</li>
            <li>二级菜单</li>
            <li>二级菜单</li>
            <li>二级菜单</li>
            <li>二级菜单</li>
        </ul>
    </li>
    <li>一级菜单<span></span>
        <ul class="sub">
            <li>二级菜单</li>
            <li>二级菜单</li>
            <li>二级菜单</li>
            <li>二级菜单</li>
            <li>二级菜单</li>
        </ul>
    </li>
    <li>一级菜单<span></span>
        <ul class="sub">
            <li>二级菜单</li>
            <li>二级菜单</li>
            <li>二级菜单</li>
            <li>二级菜单</li>
            <li>二级菜单</li>
        </ul>
    </li>
</ul>
</body>
</html>
```

#### jQuery下拉菜单

**在jQuery中如果需要执行动画，建议在执行动画之前先调用stop方法，然后再执行动画。**

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <style>
        *{
            margin: 0;
            padding:0;
        }
        .nav{
            list-style: none;
            width: 300px;
            height: 50px;
            background: brown;
            margin: 100px auto;
        }
        .nav>li{
            width: 100px;
            height: 50px;
            line-height: 50px;
            text-align: center;
            float: left;
        }
        .sub{
            list-style: none;
            background-color: pink;
            display: none;
        }
    </style>
    <script src="js/jquery-1.12.4.js"></script>
    <script>
        $(function () {
            $(".nav>li").mouseenter(function () {
                var $sub = $(this).children(".sub");
                $sub.stop();
                $sub.slideDown(1000);
            });
            $(".nav>li").mouseleave(function () {
                var $sub = $(this).children(".sub");
                $sub.stop();
                $sub.slideUp(1000);
            });
        });
    </script>
</head>
<body>
<ul class="nav">
    <li>一级菜单
        <ul class="sub">
            <li>二级菜单</li>
            <li>二级菜单</li>
            <li>二级菜单</li>
            <li>二级菜单</li>
            <li>二级菜单</li>
            <li>二级菜单</li>
            <li>二级菜单</li>
        </ul>
    </li>
    <li>一级菜单
        <ul class="sub">
            <li>二级菜单</li>
            <li>二级菜单</li>
            <li>二级菜单</li>
            <li>二级菜单</li>
            <li>二级菜单</li>
            <li>二级菜单</li>
            <li>二级菜单</li>
        </ul>
    </li>
    <li>一级菜单
        <ul class="sub">
            <li>二级菜单</li>
            <li>二级菜单</li>
            <li>二级菜单</li>
            <li>二级菜单</li>
            <li>二级菜单</li>
            <li>二级菜单</li>
            <li>二级菜单</li>
        </ul>
    </li>
</ul>
</body>
</html>
```
