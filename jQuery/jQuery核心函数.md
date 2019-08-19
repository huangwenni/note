### jQuery核心函数

- 接收一个函数

	```
        $(function () {
            alert('hello');
        });
	```

- 接收一个字符串
	- 接收一个字符串选择器(返回一个jQuery对象，对象中保存了找到的DOM元素)
	
	```
            var $box1 = $('.box1');
            var $box2 = $('#box2');
            console.log($box1);
            console.log($box2);
	```
	
	- 接收一个代码片段(返回一个jQuery对象，对象中保存了创建的DOM元素)
	
	```
            var $p = $('<p>我是段落</p>');
            console.log($p);
            $box1.append($p);
	```
	
- 接收一个DOM元素(会被包装成一个jQuery的对象并返回。)

	```
            var span = document.getElementsByTagName('span')[0];
            console.log(span);
            var $span = $(span);
            console.log($span);
	```
	
- 调用jQuery的核心函数

 	```
	$(); 
	```