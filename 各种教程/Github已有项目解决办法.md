### Project is already on Github解决办法

**起因**

在WebStrom点击Share Project on Github，显示：
Project is already on Github

**解决办法**

①进入gitbook项目目录，开启显示隐藏功能。

②点开隐藏文件夹/.git，打开其中的config文件。
![8.png](attachments/8.png)

③删除以下格式的代码：
```
[remote "origin"]
url = git@github.com:/huangwenni/note.git
fetch = +refs/heads/*:refs/remotes/origin/*
[remote "github"]
url = git@github.com:/huangwenni/note.git
fetch = +refs/heads/*:refs/remotes/github/*
[remote "note"]
url = git@github.com:/huangwenni/note.git
fetch = +refs/heads/*:refs/remotes/note/*
[remote "note1"]
url = git@github.com:/huangwenni/note.git
fetch = +refs/heads/*:refs/remotes/note1/*
[branch "master"]
remote = note1
merge = refs/heads/master
[remote "mybook"]
url = git@github.com:/huangwenni/note.git
fetch = +refs/heads/*:refs/remotes/mybook/*
[remote "book"]
url = git@github.com:/huangwenni/note.git
fetch = +refs/heads/*:refs/remotes/book/* 
```
