- [Http](#http)
- [简写方式](#简写方式)

### Http

在服务端默认发送的数据，其实是utf-8编码的内容。

浏览器在不知道服务器响应内容的编码的情况下会按照当前操作系统的默认编码去解析，中文操作系统默认是gbk。

解决方法：告诉浏览器发送的内容是什么编码的。
```
var http = require('http')
var server = http.createServer()
server.on('request',function (req,res) {
    var url = req.url
    if (url === '/plain'){
        //text/plain 普通文本
        res.setHeader('Content-Type','text/plain;charset=utf-8')
        res.end('<p>猫猫猫</p>')
    }else if (url === '/html'){
        //text/html格式
        res.setHeader('Content-Type','text/html;charset=utf-8')
        res.end('<p>猫猫猫</p>')
    }
})
server.listen(3000,function () {
    console.log('Server is running...')
})
```

不同的资源对应的Content-Type是不一样的。

具体可以查看：[HTTP Content-type 对照表](http://tool.oschina.net/commons)

图片不需要指定编码，一般字数数据才指定编码。
```
var http = require('http')
var fs = require('fs')

var server = http.createServer()
server.on('request',function (req,res) {
    var url = req.url
    if (url === '/'){
        fs.readFile('./resource/index.html',function (err,data) {
            if (err){
                res.setHeader('Content-Type','text/plain;charset = utf-8')
                res.end('文件读取失败，请稍后重试')
            }else {
                res.setHeader('Content-Type','text/html;charset = utf-8')
                res.end(data)
            }
        })
    }else if (url === '/img) {
        fs.readFile('./resource/1.jpg',function (err,data) {
            if (err){
                res.setHeader('Content-Type','text/plain;charset = utf-8')
                res.end('文件读取失败，请稍后重试')
            }else {
                res.setHeader('Content-Type','image/jpeg')
                res.end(data)
            }
        })
    }
})

server.listen(3000,function () {
    console.log('启动成功')
})
```

### 简写方式

```
http
    .createServer(function (req,res) {

    })
    .listen(3000,function () {
        console.log('running...')
    })
```








