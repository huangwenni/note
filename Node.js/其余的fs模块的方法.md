###  其余的fs模块的方法
#### fs.readdir

以异步方式读取文件目录。

接收参数：

path：目录路径

callback：回调。传递两个参数 err 和 files，files是一个包含 “ 指定目录下所有文件名称的” 数组。

```
var fs = require('fs')
fs.readdir('D:/程序媛的个人空间mmmmmmm/node学习/app/www',function (err,files) {
    if (err){
        return console.log('目录不存在')
    }
    console.log(files)
})
```
