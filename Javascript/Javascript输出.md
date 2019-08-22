- [javascript输出](#javascript输出)
	- [alert](#alert)
	- [document.write](#documentwrite)
	- [console.log](#consolelog)
	- [innerHTMl](#innerhtml)
- [prompt](#prompt)

### javascript输出

#### alert

**作用**

控制浏览器弹出一个警告框。

**例子**

```
alert(“哈哈哈”);
```

#### document.write

**作用**

向body中写内容。

**例子**

```
Document.write(“哈哈哈”);
```

#### console.log

**作用**

向控制台输出内容。

**例子**

```
console.log(“哈哈哈”);
```

#### innerHTMl

**作用**

如需访问 HTML 元素，可使用 document.getElementById(id) 方法。

id 属性定义 HTML 元素。innerHTML 属性定义 HTML 内容。

**例子**

```
<p id = "demo"></p>
<script>
   document.getElementById("demo").innerHTML = "小猫";
</script>
```

### prompt

prompt()可以弹出一个提示框，该提示框中会带有一个文本框，用户可以在文本框中输入一段内容。

该函数需要一个字符串作为参数，该字符串将会作为提示框的提示文字。用户输入的内容将会作为函数的返回值返回，可以定义一个变量来接收该内容。

prompt()函数的返回值是String类型的。

```
var score = prompt(“请输入小明的期末成绩：”);
alert(score);
```

