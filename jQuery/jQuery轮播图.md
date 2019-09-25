- [jQuery轮播图](#jquery轮播图)
	- [无限循环滚动](#无限循环滚动)

### jQuery轮播图

#### 无限循环滚动

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
            width: 880px;
            height: 248px;
            border: 1px solid #000;
            margin: 100px auto;
            overflow: hidden;
        }
        ul{
            list-style: none;
            width: 2640px;
            height: 248px;
            background: #000000;
        }
        ul>li{
            float: left;
        }
    </style>
    <script src="js/jquery-1.12.4.js"></script>
    <script>
        $(function () {
            var offset = 0;
            var timer;
            function autoPlay(){
                timer = setInterval(function () {
                    offset += -10;
                    if (offset <= -1760) {
                        offset = 0;
                    }
                    $("ul").css("marginLeft",offset);
                },50);
            }
            autoPlay();
            //监听li的移入事件
            $("li").hover(function () {
                //停止滚动
                clearInterval(timer);
                //给非当前选中添加蒙版 li变透明就会看到ul的背景
                $(this).siblings().fadeTo(100,0.5);
                $(this).fadeTo(100,1);
            },function () {
                //继续滚动
                autoPlay();
                //去除所有的蒙版
                $("li").fadeTo(100,1);
            });
        });
    </script>
</head>
<body>
<div>
    <ul>
        <li><img src="images/2.jpg" alt=""> </li>
        <li><img src="images/3.jpg" alt=""> </li>
        <li><img src="images/4.jpg" alt=""> </li>
        <li><img src="images/5.jpg" alt=""> </li>
        <li><img src="images/2.jpg" alt=""> </li>
        <li><img src="images/3.jpg" alt=""> </li>
    </ul>
</div>
</body>
</html>
```