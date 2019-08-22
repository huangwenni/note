- [BOM浏览器对象模型](#BOM浏览器对象模型)
	- [Window](#window)
	- [Navigator](#navigator)
		- [userAgent](#userAgent)
	- [Location](#location)
		- [assign()](#assign)
		- [reload()](#reload)
		- [replace()](#replace)
	- [ History](#history)
		- [history.length](#historylength)
		- [back()](#back)
		- [forward()](#forward)
		- [go()](#go)
	- [Screen](#screen)

### BOM浏览器对象模型

- BOM可以使我们通过JS来操作浏览器，在BOM中为我们提供了一组对象，用来完成对浏览器的操作。
- 这些BOM对象在浏览器中都是作为window对象的属性保存的，可以通过window对象来使用，也可以直接使用。

#### Window

代表的是整个浏览器的窗口，同时window也是网页中的全局对象。

#### Navigator

- 代表的当前浏览器的信息，通过该对象可以来识别不同的浏览器。
- 由于历史原因，Navigator对象中的大部分属性都已经不能帮助我们识别浏览器了，一般我们只会使用userAgent来判断浏览器的信息。
- 如果通过UserAgent不能判断，还可以通过一些浏览器中特有的对象，来判断浏览器的信息。

##### userAgent

userAgent是一个字符串，这个字符串中包含有用来描述浏览器信息的内容，不同的浏览器会有不同的userAgent。

```
			var ua = navigator.userAgent;
			console.log(ua);

			if(/firefox/i.test(ua)){
				alert("你是火狐");
			}else if(/chrome/i.test(ua)){
				alert("你是Chrome");
			}else if(/msie/i.test(ua)){
				alert("你是IE");
			}else if("ActiveXObject" in window){
				alert("你是IE11");
			}
```

#### Location

代表当前浏览器的地址栏信息，通过Location可以获取地址栏信息，或者操作浏览器跳转页面。

如果直接打印location，则可以获取到地址栏的信息（当前页面的完整路径）。

```
alert(location);
```

如果直接将location属性修改为一个完整的路径，或相对路径，则我们页面会自动跳转到该路径，并且会生成相应的历史记录。

```
location = "http://www.baidu.com";
location = "01.BOM.html";
```

##### assign()

用来跳转到其他的页面，作用和直接修改location一样。

##### reload()

用于重新加载当前页面，作用和刷新按钮一样。

如果在方法中传递一个true，作为参数，则会强制清空缓存刷新页面。

```
location.reload(true);
```

##### replace()

可以使用一个新的页面替换当前页面，调用完毕也会跳转页面，不会生成历史记录，不能使用回退按钮回退。

```
location.replace("01.BOM.html");
```

#### History

代表浏览器的历史记录，可以通过该对象来操作浏览器的历史记录。由于隐私原因，该对象不能获取到具体的历史记录，只能操作浏览器向前或向后翻页。

而且该操作只在当次访问时有效。

##### history.length

属性，可以获取到当成访问的链接数量。

```
alert(history.length);
```

##### back()

可以用来回退到上一个页面，作用和浏览器的回退按钮一样。

```
history.back();
```

##### forward()

可以跳转下一个页面，作用和浏览器的前进按钮一样。

```
history.forward();
```

##### go()

- 可以用来跳转到指定的页面。
- 它需要一个整数作为参数
	- 1：表示向前跳转一个页面，相当于forward()。
	- 2：表示向前跳转两个页面。
	- -1：表示向后跳转一个页面。
	- -2：表示向后跳转两个页面。

```
history.go(-1);
```

#### Screen

代表用户的屏幕的信息，通过该对象可以获取到用户的显示器的相关的信息。