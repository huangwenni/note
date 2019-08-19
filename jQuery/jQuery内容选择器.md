### jQuery内容选择器


先设置body：
```
<body>
<div></div>
<div>div1</div>
<div>div2</div>
<div><span></span></div>
<div><p></p></div>
</body>
```

设置style样式：
```
        <style>
            div{
                width: 50px;
                height: 100px;
                background: red;
                margin-top:5px;
            }
        </style>
```

- `:empty`
	- 作用：找到既没有文本内容，也没有子元素的指定元素。
	
```
                var $div = $('div:empty');
                console.log($div);
```

- `:parent`
	- 作用：找到有文本内容或有子元素的指定元素。

```
                var $div = $('div:parent');
                console.log($div);
```

- `:contains(text)`
	- 作用：找到包含指定文本内容的指定元素。

```
                var $div = $("div:contains('div1')");
                console.log($div);
```

- `:has(selector)`
	- 作用：找到包含指定子元素的指定元素。

```
                var $div = $("div:has('span')");
                console.log($div);
```


