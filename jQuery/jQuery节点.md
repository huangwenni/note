### jQuery节点

- [jQuery节点](#jquery节点)
	- [ jQuery添加节点相关的方法](#jquery添加节点相关的方法)
	- [jQuery删除节点相关的方法](#jquery删除节点相关的方法)
	- [jQuery替换节点相关的方法](#jquery替换节点相关的方法)
	- [jQuery复制节点相关的方法](#jquery复制节点相关的方法)

#### jQuery添加节点相关的方法

- 内部插入
	- append(content|fn)、appendTo(content)
		- 会将元素添加到指定元素内部的最后。
	- prepend(content|fn)、prependTo(content)
		- 会将元素添加到指定元素内部的最前面。
- 外部插入
	- after(content|fn)、insertAfter(content)
		- 会将元素添加到指定元素外部的后面。
	- before(content|fn)、insertBefore(content)
		- 会将元素添加到指定元素外部的前面。

body中的代码：

```
<button>添加节点</button>
<ul>
    <li>我是第1个li</li>
    <li>我是第2个li</li>
    <li>我是第3个li</li>
</ul>
<div></div>
```

```
                $("button").click(function () {
                    var $li = $("<li>新增的li</li>");
                    
                    //$("ul").append($li);
                    //$li.appendTo("ul");
                    //$("ul").prepend($li);
                    //$li.prependTo("ul");
                    

                    //$("ul").after($li);
                    //$("ul").before($li);
                    //$li.insertAfter("ul");
                    $li.insertBefore("ul");
                })
```

#### jQuery删除节点相关的方法

- remove([expr])、detach([expr])
	- 删除指定元素。
- empty()
	- 删除指定元素的内容和子元素，指定元素自身不会被删除。

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <script src="js/jquery-1.12.4.js"></script>
    <script>
        $(function () {
            $("button").click(function () {
                //$("div").remove();
                //$("li").detach(".item");
                $("div").empty();
            });
        });
    </script>
</head>
<body>
<button>删除节点</button>
<ul>
    <li class="item">我是第1个li</li>
    <li>我是第2个li</li>
    <li class="item">我是第3个li</li>
    <li>我是第4个li</li>
    <li class="item">我是第5个li</li>
</ul>
<div>我是div
    <p>我是段落</p>
</div>
</body>
</html>
```

#### jQuery替换节点相关的方法

- replaceWith(content|fn)、replaceALL(selector)
	- 替换所有匹配的元素为指定的元素。

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <script src="js/jquery-1.12.4.js"></script>
    <script>
        $(function () {
            $("button").click(function () {
                //新建一个元素
                var $h6 = $("<h6>我是标题6</h6>");
                //替换元素
                //$("h1").replaceWith($h6);
                $h6.replaceAll("h1");
            });
        });
    </script>
</head>
<body>
<button>替换节点</button>
<h1>我是标题1</h1>
<h1>我是标题1</h1>
<p>我是段落</p>
</body>
</html>
```

#### jQuery复制节点相关的方法

- clone([Event[,deepEven]])
	- 如果传入false就是浅复制，如果传入true就是深复制。
	- 浅复制只会复制元素，不会复制元素的事件。
	- 深复制会复制元素，而且还会复制元素的事件。

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <script src="js/jquery-1.12.4.js"></script>
    <script>
        $(function () {
            $("button").eq(0).click(function () {
                //浅复制一个元素
                var $li = $("li:first").clone(false);
                //将复制的元素添加到ul中
                $("ul").append($li);
            });
            $("button").eq(1).click(function () {
                //深复制一个元素
                var $li = $("li:first").clone(true);
                //将复制的元素添加到ul中
                $("ul").append($li);
            });
            $("li").click(function () {
                alert($(this).html());
            });
        });
    </script>
</head>
<body>
<button>浅复制节点</button>
<button>深复制节点</button>
<ul>
    <li>我是第1个li</li>
    <li>我是第2个li</li>
    <li>我是第3个li</li>
    <li>我是第4个li</li>
    <li>我是第5个li</li>
</ul>
</body>
</html>
```






