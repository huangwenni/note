### var、let和const

- var
	- 可以重复声明。
	- 无法限制修改。
	- 没有块级作用域。
- let
	- 不能重复声明。
	- 声明变量，可以修改。
	- 有块级作用域。
- const
	- 不能重复声明。
	- 声明常量，不能修改。
	- 有块级作用域

```
        if (true){
            let a = 2;
        }
        console.log(a);     //会报错
```
```
        {
            let a = 12;
        }
        console.log(a);      //会报错
```
```
        if (true){
            const a = 2;
        }
        console.log(a);     //会报错
```
```
        {
            const  a = 12;
        }
        console.log(a);      //会报错
```
	