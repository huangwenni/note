- [CSS3](css3)
	- [CSS3圆角边框](#css3圆角边框)
	- [CSS3背景透明](#css3背景透明)

### CSS3
#### CSS3圆角边框
```
border-radius:50%;   让一个正方形变成圆
border-radius:1px 1px 1px 1px;  左上 右上 右下 左下
border-radius:10px 0; 左上 右下 右上 左下
border-radius: 10px 30px 50px; //左上 右上左下 右下
```
#### CSS3背景透明
```
div{
	width:200px;
	height:200px;
	color:#fff;
	background:rgba(0,0,0,0.3); //red green blue alpha 0~1（alpha是透明度）
}
```
```
background:transparent;
```