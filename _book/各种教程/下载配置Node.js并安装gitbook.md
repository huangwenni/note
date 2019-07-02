### 下载Node.js并配置
#### 在官网上下载Node.js
[Download \| Node.js](https://nodejs.org/en/download/)

**检验是否成功**

打开cmd  输入node  -v     npm –v

![1.png](attachments\1.png)
#### 使用前的准备工作
在安装目录下创建两个文件夹node_global和node_cache，主要防止执行其他安装命令时候将东西安装在C盘里面，希望将全模块所在路径和缓存路径放在我node.js安装的文件夹中。 

新建文件后执行下面语句：

![2.png](attachments\2.png)
#### 安装gitbook
**在Node.js安装目录下全局安装gitbook**

cd D:\Node.js

npm install gitbook-cli –g

**在Node.js安装目录下输入mkdir mybook 创建文件夹**

**初始化**

进入 D:\Node.js\mybook

输入gitbook init 初始化目录文件

输入gitbook build 成功安装

