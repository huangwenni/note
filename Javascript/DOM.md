- [简介](#简介)
	- [节点](#节点)
	- [事件](#事件)
	- [文档的加载](#文档的加载)
- [获取元素节点](#获取元素节点)
	- [getElementById](#getelementbyid)
	- [getElementsByTagName](#getelementsbytagname)
	- [getElementsByName](#getelementsbyname)
	- [图片切换练习](#图片切换练习)
- [获取元素的子节点](#获取元素的子节点)
	- [getElementByTagName](#getelementbytagname)
	- [childNodes](#childnodes)
	- [firstChild](#firstchild)
	- [lastChild](#lastchild)
- [获取父节点和兄弟节点](#获取父节点和兄弟节点)
	- [parentNode](#parentnode)
	- [previousSibling](#previoussibling)
	- [nextSibling](#nextsibling)
- [全选练习](#全选练习)
- [DOM查询的其他方法](#查询的其他方法)
- [DOM增删改](#增删改)
- [读取和修改元素样式](#读取和修改元素样式)
	- [style](#style)
	- [currentStyle](#currentstyle)
	- [getComputedStyle](#getcomputedstyle)
	- [解决方式](#解决方式)
	- [注意](#注意)
- [其他样式操作的属性](#其他样式操作的属性)
- [练习--移动显示div内的坐标](#练习--移动显示div内的坐标)
- [练习--div跟随鼠标移动](#练习--div跟随鼠标移动)

### 简介

- DOM，全称Document Object Model文档对象模型。
- JS中通过DOM来对HTML文档进行操作，只要理解了DOM就可以随心所欲操作WEB页面。
- 文档：文档表示的就是整个的HTML网页文档。
- 对象：对象表示将网页中的每一个部分都转换为了一个对象。
- 模型：使用模型来表示对象之间的关系，这样更方便我们获取对象。

#### 节点

- 节点Node，是构成网页（HTML文档）的最基本的组成部分，网页中的每一个部分都可以称为是一个节点。
- 节点的具体类型是不同的，节点的类型不同，属性和方法也都不尽相同。
- 文档节点：整个HTML文档。
- 元素节点：HTML文档中的HTML标签。
- 属性节点：元素的属性。
- 文本节点：HTML标签中的文本内容。

**获取对象**

- 浏览器已经为我们提供文档节点对象，这个对象是window属性。
- 可以在页面中直接使用，文档节点代表的是整个网页。

#### 事件

- 事件，就是文档或浏览器窗口中发生的一些特定的交互瞬间。
- 可以在事件对应的属性中设置一些JS代码，当事件被触发时，这些代码将会执行。这种写法称为结构和行为耦合，不方便维护，不推荐使用。

```
<button id = "btn" onclick = "alert('你已点击');" >我是一个按钮</button>
```

- 可以为按钮的对应事件绑定处理函数的形式来响应事件。这样当事件被触发时，其对应的函数将会被调用。

```
<body>
    <button id = "btn" >我是一个按钮</button>
    <script>
		var btn = document.getElementById("btn");
        //绑定一个单击事件
        //像这种为单击事件绑定的函数，称为单击响应函数
        btn.onclick = function(){
            alert("你已点击");
        };
        console.log("btn");
    </script>
</body>
```

#### 文档的加载

浏览器在加载一个页面时，是按照自上向下的顺序加载的，如果将script标签写到页面上边，在代码执行时，页面还没有加载，页面没有加载的DOM对象也没有加载，会导致无法获取到DOM对象。

**解决方式一：将script标签放到body的最下方。**

**解决方式二：为window绑定一个onload事件。**

onload事件会在整个页面加载完成之后才触发，该事件对应的响应函数将会在页面加载之后执行，这样可以确保代码执行时所有的DOM对象已经加载完毕了。

```
<script>
        //获取id为btn的按钮
			window.onload = function () {
            var btn = document.getElementById("btn");
            btn.onclick = function () {
                alert("hello");
            };
        };
</script>
```

### 获取元素节点

（以下方法通过document对象调用）

#### getElementById

通过id属性获取一个元素节点对象。

#### getElementsByTagName

通过标签名获取一组元素节点对象。

#### getElementsByName

通过name属性获取一组元素节点对象。

- **innerHTML**
	- innerHTML是用于获取元素内部的HTML代码的。
	- 对于自结束标签，这个属性没有意义。
	- 如果需要读取元素节点的属性，直接使用` 元素.属性名`。
		- 注意
			- class属性不能采用这种方式，读取class属性时需要使用元素,className

```
<!DOCTYPE html>
<html lang=en>
<head>
    <meta charset=UTF-8>
    <title>Title</title>
</head>
<script>
    window.onload = function () {

        var  btn01 = document.getElementById("btn01");
        btn01.onclick = function () {
            var bj = document.getElementById("bj");
            alert(bj.innerHTML);
        };

        var btn02 = document.getElementById("btn02");
        btn02.onclick = function () {
            //这个方法会给我们返回一个类数组对象，所有查询到的元素都会封装到数组对象中
            var lis = document.getElementsByTagName("li");
            alert(lis.length);      //2
            for (var i = 0; i<lis.length;i++) {
                alert(lis[i].innerHTML);
            }
        };

        var btn03 = document.getElementById("btn03");
        btn03.onclick = function () {
            var inputs = document.getElementsByName("gender");
            alert(inputs);
            alert(inputs.length);       //2
            for (var i = 0; i < inputs.length;i++){
                alert(inputs[i].value);
                alert(inputs[i].className);
            }
        };
    };
</script>
</head>

<body>
<button id="btn01">点击我</button>
<button id="btn02">点击我</button>
<button id="btn03">点击我</button>
<ul>
    <li id ="bj">北京</li>
    <li id ="sh">上海</li>
</ul>
<input type="radio" class="a" name="gender" value="male"/>
<input type="radio" class="a" name="gender" value="female"/>
</body>
</html>
```

#### 图片切换练习

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <style>
        *{
            margin:0;
            padding:0;
        }
        img{
            width:500px;
            height:100px;
            margin:10px;
        }
        #outer{
            width:520px;
            height:180px;
            background-color: pink;
            margin:0 auto;
            text-align:center;
        }
    </style>
    <script>
        window.onload = function () {
            //点击按钮切换图片
            //获取两个按钮
            var prev = document.getElementById("prev");
            var next = document.getElementById("next");

            //要切换图片，就是要修改img的src属性
            var img = document.getElementsByTagName("img")[0];

            //创建一个数组用来保存图片的路径
            var imgArr = ["1.jpg","2.jpg","3.jpg","4.jpg","5.jpg"];

            //创建一个变量，来保存当前正在显示的图片的索引
            var index = 0;

            //设置提示文字
            //获取id为info的p元素
            var info = document.getElementById("info");
            info.innerHTML = "一共"+imgArr.length+"张图片，当前第"+ (index+1) +"张";

            prev.onclick = function () {
               //切换到上一张，索引自减
                index--;
                //判断index是否小于0
                if(index<0){
                    index = imgArr.length-1;
                }
                img.src = imgArr[index];
                info.innerHTML = "一共"+imgArr.length+"张图片，当前第"+ (index+1) +"张";
            };

            next.onclick = function () {
                //切换到下一张
                index++;
                if (index>imgArr.length-1){
                    index = 0;
                }
                img.src = imgArr[index];
                info.innerHTML = "一共"+imgArr.length+"张图片，当前第"+ (index+1) +"张";
            };
        };
    </script>
</head>
<body>
<div id="outer">
    <p id="info"></p>
    <img src="1.jpg"/>
    <button id = "prev">上一张</button>
    <button id = "next">下一张</button>
</div>
</body>
</html>
```

### 获取元素的子节点

（通过具体的元素节点调用）

body内的代码（以下方法都一样）：

```
<button id="btn04">btn04</button>
<button id="btn05">btn05</button>
<button id="btn06">btn06</button>
<ul id="city">
    <li>上海</li>
    <li>东京</li>
    <li>首尔</li>
</ul>
<ul id="phone">
    <li>上海</li>
    <li>东京</li>
    <li>首尔</li>
</ul>
```

#### getElementByTagName

方法，返回当前节点的指定标签后代节点。

```
            var  btn04 = document.getElementById("btn04");
            btn04.onclick = function () {
                var city = document.getElementById("city");
                //查找#city下所有的li节点
                var lis = city.getElementsByTagName("li");
                for (var i=0;i<lis.length;i++){
                    alert(lis[i].innerHTML);
                }
            };
```

#### childNodes

属性，表示当前节点的所有子节点。

- childNodes属性会获取包括文本节点在内的所有节点。
- 根据DOM标准，标签间的空白也会被当成文本节点。
- 在IE8及IE8以下的浏览器中，不会将空白文本当成节点。


- **children属性**
	- children属性可以获取当前元素的所有子元素(所有浏览器都兼容，推荐使用)。

```
            var btn05 = document.getElementById("btn05");
            btn05.onclick = function () {
                var city = document.getElementById("city");

                //注意：在IE8下的浏览器中，不会将空白文本当成节点，所以该属性在IE8中会返回3个子元素，在其他浏览器是7个
                var cns = city.childNodes;
                //alert(cns.length);        //7
                console.log(cns);       //NodeList(7) [text, li, text, li, text, li, text]

                //children属性可以获取当前元素的所有子元素(所有浏览器都兼容，推荐使用)
                var cns2 = city.children;
                alert(cns2.length);       //3
                console.log(cns2);      //HTMLCollection(3) [li, li, li]
            };
```

#### firstChild

属性，表示当前节点的第一个子节点（包括空白的文本节点）。

- **firstElementChild**
	- 获取当前元素的第一个子元素。
	- 不支持ie8及以下的浏览器，如果需要兼容，尽量不要使用。

```
            var btn06 = document.getElementById("btn06");
            btn06.onclick = function () {
                //返回#phone的第一个子节点
                var phone = document.getElementById("phone");
                var fir = phone.firstChild;

                fir = phone.firstElementChild;
                alert(fir);
            }
```

#### lastChild

属性，表示当前节点的最后一个子节点。

### 获取父节点和兄弟节点

（通过具体的节点调用）

#### parentNode

属性，表示当前节点的父节点。

#### previousSibling

属性，表示当前节点的前一个兄弟节点（也可能获取到空白的文本）。

- **previousElementSibling**
	- 获取前一个兄弟元素（不包括空白的文本，IE8及以下不支持）。

#### nextSibling

属性，表示当前节点的后一个兄弟节点。

- **innerText**
	- 该属性可以获取到元素内部的文本内容。
	- 和innerHTML类似，不同的是它会自动将html标签去除。

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>
<script>
    window.onload = function () {
        function myClick(idStr,fun) {
            var  btn = document.getElementById(idStr);
            btn.onclick = fun;
        }

        myClick("btn07",function () {
            var bj = document.getElementById("bj");
            //获取bj的父节点
            var pn = bj.parentNode;

            alert(pn.innerHTML);
            //弹出：
            /*
                     <li>上海</li>
                     <li>东京</li>
                     <li>首尔</li>
                     <li id="bj">北京</li>
             */

            //alert(pn.innerText);
            /*
            * 弹出
            *       上海
            *       东京
            *       首尔
            *       北京
            * */
        });

        myClick("btn08",function () {
            var and = document.getElementById("android");
            //返回#android的前一个兄弟节点（也可能获取到空白的文本）
            var ps = and.previousSibling ;

            //获取前一个兄弟元素（不包括空白的文本，IE8及以下不支持）
            var pe = and.previousElementSibling;
            alert(pe);
        });

        //返回#bj的文本值
        myClick("btn11",function () {
            var bj = document.getElementById("bj");

            alert(bj.innerHTML);
            //弹出北京

            var fc = bj.firstChild;
            alert(fc.nodeValue);
            //弹出北京

            alert(bj.firstChild.nodeValue);
            //弹出北京
        });
    };
</script>

<button id="btn07">btn07</button>
<button id="btn08">btn08</button>
<button id="btn11">btn11</button>

<ul id="city">
    <li>上海</li>
    <li>东京</li>
    <li>首尔</li>
    <li id="bj">北京</li>
</ul>
<ul>
    <li>IOS</li>
    <li id="android">android</li>
</ul>
<input type="text" id="username" value="abcde"/>
</body>
</html>
```

### 全选练习

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <script>
        window.onload = function () {
            //获取四个多选框items
            var items = document.getElementsByName("items");
            //获取全选/全不选多选框
            var checkedAllBox = document.getElementById("checkedAllBox");
            var checkedAllBtn = document.getElementById("checkedAllBtn");

            checkedAllBtn.onclick = function () {
                //遍历items
                for (var i = 0;i<items.length;i++){
                    //通过多选框的checked属性可以获取或设置多选框的选中状态
                    //设置四个多选框为选中状态
                    items[i].checked = true;
                }
                //将全选/全不选设置为选中
                checkedAllBox.checked = true;
            };

            var checkedNoBtn = document.getElementById("checkedNoBtn");
            checkedNoBtn.onclick = function () {
                var items = document.getElementsByName("items");
                for (var i = 0;i<items.length;i++){
                    items[i].checked = false;
                }
                checkedAllBox.checked = false;
            };

            var checkedRevBtn = document.getElementById("checkedRevBtn");
            checkedRevBtn.onclick = function () {
                checkedAllBox.checked = true;

                for (var i = 0;i<items.length;i++){
                    /*
                    if (items[i].checked){
                        items[i].checked = false;
                    } else{
                        items[i].checked = true;
                    }
                    */
                    items[i].checked = !items[i].checked;
                    //判断四个多选框是否全选
                    //是要有一个没选中就不是全选
                    if (!items[i].checked) {
                        checkedAllBox.checked = false;
                    }
                }
                //在反选时，也需要判断四个多选框是否选中
                //将checkedbox设置为选中状态
            };
            //点击提交按钮以后，将所有选中的多选框的value属性值弹出
            var sendBtn = document.getElementById("sendBtn");
            sendBtn.onclick = function () {
                var items = document.getElementsByName("items");
                for (var i = 0;i<items.length;i++){
                    if (items[i].checked){
                        alert(items[i].value);
                    }
                }
            };
            //全选/全不选多选框
            //在事件响应函数中，响应函数是给谁绑定的this就是谁
            checkedAllBox.onclick = function () {
                var items = document.getElementsByName("items");
                for(var i = 0;i<items.length;i++){
                    items[i].checked= this.checked;
                }
            };

            /*
            * 如果四个多选框全都选中，则checkedAllBox也都选中，否则不选中
            * */

            //为四个多选框分别绑定单击响应函数
            for (var i = 0 ;i<items.length;i++) {
                items[i].onclick = function () {
                    //将checkedbox设置为选中状态
                    checkedAllBox.checked = true;
                    for (var j = 0;j<items.length;j++){
                        //判断四个多选框是否全选
                        //是要有一个没选中就不是全选
                        if (!items[j].checked) {
                            checkedAllBox.checked = false;
                            //一旦进入判断，就已经得出结果，不用再继续循环
                            break;
                        }
                    }
                }
            }
        };
    </script>
</head>
<body>
<form method="post" action="">
    你爱好的运动是<input type="checkbox" id = "checkedAllBox"/>全选/全不选
    <br/>
    <input type="checkbox" name="items" value="足球"/>足球
    <input type="checkbox" name="items" value="篮球">篮球
    <input type="checkbox" name="items" value="乒乓球">乒乓球
    <input type="checkbox" name="items" value="羽毛球">羽毛球
    <br/>
    <input type="button" id="checkedAllBtn" value="全选"/>
    <input type="button" id="checkedNoBtn" value="全不选"/>
    <input type="button" id="checkedRevBtn" value="反选"/>
    <input type="button" id="sendBtn" value="提交"/>
</form>
</body>
</html>
```

### 查询的其他方法

- document.body
	- 在document中有一个属性body，它保存的是body的引用。
- document.documentElement
	- document.documentElement保存的是html根标签。
- document.all
	- document.all代表页面中所有的元素。
	- document.getElementsByTagName("\*")与上面的效果相同。
- getElementsByClassName
	- 根据元素的class属性值查询一组元素节点对象，该方法不支持IE8以下的浏览器。
-  document.querySelector
	- document.querySelector(）需要一个选择器的字符串作为参数，可以根据一个CSS选择器来查询一个元素节点对象。
	- 虽然IE8中没有getElementsByClassName()，但是可以使querySelector()代替，使用该方法总会返回唯一的一个元素，如果满足条件的元素的有多个，只会返回第一个。
- document.querySelectorAll
	- document.querySelectorAll()该方法和querySelctor()用法类似，不同的是它会将符合条件的元素封装到一个数组中返回，即使符合条件的元素只有一个，也会返回数组。

### 增删改

- document.createElement
 	- 用于创建一个元素节点对象，需要一个标签名作为参数，将会根据该标签名创建元素节点对象，并将创建好的对象作为返回值返回。
- document.createTextNode
 	- 可以用来创建一个文本节点对象，需要一个文本内容作为参数，将会根据该内容创建文本节点，并将新的节点返回。
- appendChild
	 - 向一个父节点中添加一个新的子节点。

	```
	var li = document.createElement("li");
	var gztext = document.createTextNode("广州");
	li.appendChild(gztext);
	```

- insertBefore
	 - 在指定的子节点前面插入新的子节点。

	```
	父节点.insertBefore(新节点，旧节点)
	```

- replaceChild
	 - 可以使用指定的子节点替换已有的节点。
- removeChild
 	- 删除一个子节点。
	 - 方法一：
	```
	父节点.removeChild(子节点);
	```
	- 方法二：
	```
	子节点.parentNode.removeChild(bj);
	```

**用innerHTML也可以完成DOM的增删改的一些操作，一般会两种方式结合使用**

**推荐写法**

向后添加广州：

```
  myClick("btn05",function () {
            var city = document.getElementById("city");
            //创建一个li
            var li = document.createElement("li");
            //向li中设置文本
            li.innerHTML = "广州";
            //将li添加到city中
            city.appendChild(li);
        });
```

### 读取和修改元素样式

#### style

- 如果CSS的样式名中含有` -`，这种名称在JS是不合法的，需要将这种样式名修改为驼峰命名法，去掉 - ，然后将 - 后的字母大写。
- 通过style属性设置和读取的样式都是内联样式，无法设置和读取样式表中的样式，内联样式有较高的优先级，所以通过JS修改的样式往往会立即显示。

修改元素样式：

```
元素.style.样式名 = 样式值
```
读取元素样式：

```
元素.style.样式名 = 样式值
```

```
<body>
<script>
    window.onload = function () {

        //点击按钮以后，修改box1的大小
        var box1 = document.getElementById("box1");
        var box01 = document.getElementById("box01");
        btn01.onclick = function () {
            //修改box1的样式
            box1.style.width = "300px";
            box1.style.height = "300px";
            box1.style.backgroundColor = "yellow";
        };

        //点击按钮2后，读取元素样式
        var btn02 = document.getElementById("btn02");
        btn02.onclick = function () {
            alert(box1.style.backgroundColor);
        };
    };

</script>
<button id = "btn01">点我一下</button>
<button id = "btn02">点我一下2</button>
<div id = "box1"></div>
</body>
```

#### currentStyle

- 可以用来读取当前元素显示的样式，如果当前元素没有设置该样式，会获取默认值。
- 只有ie支持，其他浏览器都不支持。

```
元素.currentStyle.样式名
```

```
<div id="box1"></div>
<script>
    alert(box1.currentStyle.backgroundColor);
</script>
```

#### getComputedStyle

- 在其他浏览器中使用getComputedStyle()方法来获取元素当前的样式。这个方法是window的方法，可以直接使用。
- 需要两个参数
	- 第一个，要获取样式的元素。
	- 第二个，可以传递一个伪元素，一般都传null。
- 该方法会返回一个对象，对象中封装了当前元素对应的样式，可以通过`对象.样式名`来读取样式。如果获取的样式没有设置，则会获取到真实的值而不是默认值（比如：没有设置width，它不会获取到auto，而是一个长度）。
- 该方法不支持IE8及以下的浏览器。

```
    var obj = getComputedStyle(box1,null);
    alert(obj.width);
    //两种都可以
    alert(getComputedStyle(box1,null).width);
```

#### 解决方式

```
    function getStyle(obj,name) {
        //没加window的时候，是一个变量，需要在作用域中寻找，变量没找到会报错
        //加了window，变成对象的属性，属性没找到会返回undefined

        /*
        if (window.getComputedStyle) {
            return getComputedStyle(obj,null)[name];
        }else{
            return obj.currentStyle[name];
        }
        */

        /*
        //建议使用上面那种方法，下面这种在两种方法都可以使用的时候会优先选择currentStyle
        if (obj.currentStyle) {
            return obj.currentStyle[name];
        }else{
            return getComputedStyle(obj,null)[name];
        }
        */

        //效果相同
        return window.getComputedStyle?getComputedStyle(obj,null)[name]:obj.currentStyle[name];
    }
```

#### 注意

通过currentStyle和getComputedStyle读取到的样式都是只读的，不能修改，如果要修改必须通过style属性。

### 其他样式操作的属性

- clientWidth、clientHeight
	- 这两个属性可以获取元素的可见宽度和高度。
	- 这些属性都是不带px的，返回都是一个数字，可以直接进行计算。
	- 会获取元素宽度和高度，包括内容区和内边距。
	- 这些属性都是只读的，不能修改。

- offsetWidth、offsetHeight
	- 获取元素的整个的宽度和高度，包括内容区、内边距和边框。

- offsetParent
	- 会获取到离当前元素最近的开启了定位的祖先元素，如果所有的祖先元素都没有开启定位，则返回body。

- offsetLeft、offsetTop
	- 当前元素相对于其定位父元素的水平偏移量/当前元素相对于其定位父元素的垂直偏移量。

- scrollWidth、scrollHeight
	- 可以获取元素整个滚动区域的宽度和高度。

- scrollLeft、scrollTop
	- 获取水平滚动条滚动的距离/获取垂直滚动条滚动的距离。

- clientX和clientY
	- 用于获取鼠标在当前的可见窗口的坐标。div的偏移量，是相对于整个页面的。

- pageX和pageY
	- 可以获取鼠标相对于当前页面的坐标，但是这个两个属性在IE8中不支持，所以如果需要兼容IE8，则不要使用。

**公式**

当满足scrollHeight - scrollTop == clientHeight，说明垂直滚动条滚动到底。

### 练习--移动显示div内的坐标

设置两个div：

```
<div id="areaDiv"></div>
<div id="showMsg"></div>
```
```
window.onload = function () {
            var areaDiv = document.getElementById("areaDiv");
            var showMsg = document.getElementById("showMsg");

            areaDiv.onmousemove = function (event) {
                /*
                if (!event){
                    event = window.event;
                }
                */
				//下面的方式更好
                event = event||window.event;
                var x = event.clientX;
                var y = event.clientY;
                showMsg.innerHTML = "x="+x+",y="+y;
            };
        };
```

### 练习--div跟随鼠标移动

```
<body style="height: 1000px;width: 2000px;">
    <div id="box1"></div>
</body>
```

```
        window.onload = function () {
            var box1 = document.getElementById("box1");
            document.onmousemove = function (event) {
                event = event || window.event;
                /*
                 * chrome认为浏览器的滚动条是body的，可以通过body.scrollTop来获取
                 * 火狐等浏览器认为浏览器的滚动条是html的
                 */
                var st =  document.body.scrollTop||document.documentElement.scrollTop ;
                var sl = document.body.scrollLeft || document.documentElement.scrollLeft;

                var left = event.clientX;
                var top = event.clientY;
               /*
                var left = event.pageX;
                var top = event.pageY;
               */
               
               //设置div的偏移量
               box1.style.left = left + sl +"px";
               box1.style.top = top + st +"px";
    };
};
```





