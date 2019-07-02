### CSS用户界面样式
#### 鼠标经过样式
```
cursor:pointer;		/*让鼠标样式变成小手*/
cursor:text;		/*让鼠标样式变成选择*/
cursor:move;		/*让鼠标样式变成十字架*/
cursor:default;		/*鼠标变成默认的样子*/ 
```
#### 轮廓outline
经常存在于表单中。
```
input{
	outline:none;	//取消轮廓线的做法
	border:1px bolid red;	//浏览器中可能默认不一样 所以要自己设置
}
```
#### 防止拖拽文本域resize
```
textarea{
	resize:none;	/*取消文本域大小拖拽 默认可拖拽*/
	outline:none; /*取消蓝色边框*/
}
```