- [在node中使用模板引擎](#在node中使用模板引擎)
	- [在node中使用art-template模板引擎](#在node中使用art-template模板引擎)
	- [each](#each)

### 在node中使用模板引擎

#### 在node中使用art-template模板引擎

- 安装
	- 该命令在哪执行就会把包下载到哪里。默认会下载到 node_modules 目录中。
	- node_modules 不要改，也不支持改。

```
npm install art-template
```

- 加载

```
require(‘art-template’)
```

- template.render
	- 将返回渲染结果。

**在node中使用art-template模板引擎.js的代码：**

```
var template = require('art-template')
var fs = require('fs')

fs.readFile('./tpl.html',function (err,data) {
    if (err){
        return console.log('读取文件失败了')
    }
    var ret = template.render(data.toString(), {
        name: 'Sweetkitty',
        age: 22,
        province: '厦门市',
        hobbies: [
            '写代码',
            '听音乐',
            '打游戏'
        ],
        title: '个人信息'
})

    console.log(ret)    //helloJack
})
```

**tpl.html的代码：**
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>{{title}}</title>
</head>
<body>
<p>大家好，我叫：{{ name }}</p>
<p>我今年 {{ age }} 岁了</p>
<h1>我来自 {{ province }}</h1>
<p>我喜欢：{{each hobbies}} {{ $value }} {{/each}}</p>
<script>
    var foo = '{{title}}'
</script>
</body>
</html>
```

#### each

```
{{each 数组}}
<li>{{$value}}</li>
{{/each}}
```