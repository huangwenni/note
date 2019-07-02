- [点击时执行Javascript代码](#点击时执行javascript代码)
    - [将js代码编写到标签的onclick属性中](#将js代码编写到标签的onclick属性中)
    - [点击超链接时执行js代码](#点击超链接时执行js代码)
    - [点完超链接没有反应，通过js处理一些功能](#点完超链接没有反应，通过js处理一些功能)
    - [解决方案](#解决方案)
- [引入Javascript代码](#引入javascript代码)

### 点击时执行javascript代码
可以写在标签的属性中，但是他们属于结构与行为耦合，不方便维护，不推荐使用。
#### 将js代码编写到标签的onclick属性中
```
<button onclick="alert('点击效果');">按钮</button>
```
#### 点击超链接时执行js代码
```
<a href=”javascript:alert (‘点击效果’);”></a>
```
#### 点完超链接没有反应，通过js处理一些功能
```
<a href=”javascript:;”></a>

```
#### 解决方案
js代码要另外写，编写到外部的js文件中或script标签中。
### 引入javascript代码
#### 外部js文件好处
写到外部文件中可以在不同的页面中同时引用。

也可以利用到浏览器的缓存机制。
引入Javascript代码：

```
<script type=”text/javascript” src=”js/script.js”></script>
```
#### 注意
script标签一旦用于引入外部文件了，就不能用来编写代码了，浏览器会忽略。

如果需要则可以再创建一个新的script标签用于编写内部代码。



