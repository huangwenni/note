- [jQuery对象和jQuery入口函数](#jquery对象和jquery入口函数)
	- [jQuery对象](#jquery对象)
	- [jQuery入口函数的几种写法](#jquery入口函数的几种写法)


### jQuery对象和jQuery入口函数

#### jQuery对象

- 什么是jQuery对象
	- jQuery对象是一个伪数组。
- 什么是伪数组
	- 有0到length-1的属性，并且有length属性。
```
        $(function () {
            //伪数组
            var $div = $('div');
            console.log($div);

            //数组
            var arr = [1,3,5];
            console.log(arr);
        });
```

####  jQuery入口函数的几种写法

```
        //第一种
        $(document).ready(function () {
            alert('hello');
        });
        
        //第二种
        jQuery(document).ready(function () {
            alert('hello');
        });

        //第三种，推荐
        $(function () {
            alert('hello')
        });

        //第四种
        jQuery(function () {
            alert('hello');
        });
```