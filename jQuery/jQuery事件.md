- [jQuery事件](#jquery事件)
	- [jQuery事件绑定和事件移除](#jquery事件绑定和事件移除)
		- [事件绑定](#事件绑定)
		- [事件移除](#事件移除)

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



