### Node.js是什么
- Node.js 不是一门语言，不是库、不是框架。

- Node.js是一个Javascript运行时环境，可以解析和执行Javascript代码。

- 以前只有浏览器可以解析执行Javascript代码，现在的Javascript可以完全脱离浏览器来运行，一切归功于Node.js。

#### 浏览器中的Javascript
- ECMAScript基本的语法
	- if
	- var 
	- function
	- Object
	- Array
- BOM
- DOM

#### Node.js中的Javascript
- ECMAScript。
	- 没有BOM、DOM，服务端不处理页面。
- 核心模块
- 第三方模块
- 用户自定义模块

##### 核心模块
- 在Node这个Javascript执行环境中提供了一些服务器级别的操作API，这些API绝大多数都被包装到了一个具名的核心模块中了。
- 例如文件操作的`fs`核心模块，http服务构建的`http`模块，`path`路径操作模块、`os`操作系统信息模块。
- 如果想要使用，就必须：

```
//request是用来加载模块的
var fs = request('fs')
```
```
// 用来获取机器信息的
var os = require('os')

// 用来操作路径的
var path = require('path')

// 获取当前机器的 CPU 信息
console.log(os.cpus())

// memory 内存
console.log(os.totalmem())

// 获取一个路径中的扩展名部分
// extname extension name
console.log(path.extname('c:/a/b/c/d/hello.txt'))
```

#### 构建于Chrome的V8引擎之上
- 代码只是具有特定格式的字符串而已，引擎可以认识它，可以帮你去解析和执行。
- Goole Chrome的V8引擎是目前公认的解析执行Javascript代码最快的。
- Node.js的作者把Google Chrome中的V8引擎移植了出来，开发了一个独立的Javascript运行时环境。

#### Node.js特性
- event-driven 事件驱动
- non-blocking I/O model 非阻塞IO模型（异步）
- lightweight and efficient 轻量和高效

#### npm
- npm是世界上最大的开源生态系统
- 绝大多数Javascript相关的包都存放在了npm上，这样做的目的是为了让开发人员更方便去下载使用。

### Node.js能做什么
- Web服务器后台
- 命令行工具
	- npm（node）
	- git（c语言）
	- hexo（node）
- 对于前端工程师来讲，接触node最多的是它的命令行工具
	- webpack
	- gulp
	- npm

#### 预备知识
- HTML
- CSS
- JavaScript
- 简单的命令行操作
	- cd
	- dir
	- Is
	- mkdir
	- rm

#### 注意
- 文件名不要使用`Node.js`来命名