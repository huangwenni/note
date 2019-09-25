### jQuery冲突问题

- 方法一：释放$的使用权
	- 释放操作必须在编写其他jQuery代码之前编写。
	- 释放之后就不能再使用$，改为使用jQuery。

	```
        jQuery.noConflict();
        jQuery(function () {
            alert('hello');
        });
	```
	
- 方法二：自定义访问符号

	```
        var nj = jQuery.noConflict();
        nj(function () {
            alert('hello');
        });
	```



