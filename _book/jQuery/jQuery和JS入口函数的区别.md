### jQuery和JS入口函数的区别

- 原生JS和jQuery入口函数的加载模式不同。
	- 原生JS会等到DOM元素加载完毕，并且图片也加载完毕才会执行。
	- jQuery等到DOM元素加载完毕后就会执行，不需要等到图片也加载完毕。

		```
		//图片自找
        window.onload = function (ev) {
            var img = document.getElementsByTagName('img')[0];
            console.log(img);
            var width = window.getComputedStyle(img).width;
            console.log(width);							//80px
        };
		```
		```
		//注意清除缓存
        $(document).ready(function () {
            var $img = $('img')[0];
            console.log($img);
            var $width = $img.width;
            console.log($width);						//0	
        });
		```
		
	- 原生的JS如果编写了多个入口函数，后面编写的会覆盖前面的。
	- jQuery中编写多个入口函数，后面的不会覆盖前面的。

		```
        window.onload = function (ev) {
            alert('hello1');
        };

        window.onload = function (ev) {
            alert('hello2');
        };
		//只弹出hello2
		```
		```
        $(document).ready(function () {
            alert('hello 1');
        });
        $(document).ready(function () {
            alert('hello 2');
        });
		//先弹出hello 1，再弹出hello2
		```


	

