- [v-for的四种使用方式](#v-for的四种使用方式)
	- [v-for循环普通数组](#v-for循环普通数组)
	- [v-for循环对象数组](#v-for循环对象数组)
	- [v-for循环对象](#v-for循环对象)
	- [v-for迭代数字](#v-for迭代数字)
- [v-for循环中key属性的使用](#v-for循环中key属性的使用)
- [v-if和v-show的使用](#v-if和v-show的使用)

### v-for的四种使用方式
#### v-for循环普通数组
```
<body>
<div id="app">
    <!--
    <p>{{list[0]}}</p>      //1
    -->
    <p v-for="(item,i) in list">索引值:{{i}}---每一项：{{item}}</p>
</div>
<script>
    //创建一个vue的实例
    var vm = new Vue({
        el:'#app',
        data:{
            list:[1,2,3,4,5,6]
        },
        methods:{}
    })
</script>
</body>
```
页面效果如下：
```
索引值:0---每一项：1

索引值:1---每一项：2

索引值:2---每一项：3

索引值:3---每一项：4

索引值:4---每一项：5

索引值:5---每一项：6
```
#### v-for循环对象数组
```
<body>
<div id="app">
<p v-for="(item,i) in list">id:{{item.id}} --- name:{{item.name}} --- 索引：{{i}} --- 每一项：{{item}}</p>
</div>
<script>
    //创建一个vue的实例
    var vm = new Vue({
        el:'#app',
        data:{
            list:[
                {id:1,name:'zs1'},
                {id:2,name:'zs2'},
                {id:3,name:'zs3'},
                {id:4,name:'zs4'}
            ]
        },
        methods:{}
    })
</script>
</body>
```
页面效果如下：
```
id:1 --- name:zs1 --- 索引：0 --- 每一项：{ "id": 1, "name": "zs1" }

id:2 --- name:zs2 --- 索引：1 --- 每一项：{ "id": 2, "name": "zs2" }

id:3 --- name:zs3 --- 索引：2 --- 每一项：{ "id": 3, "name": "zs3" }

id:4 --- name:zs4 --- 索引：3 --- 每一项：{ "id": 4, "name": "zs4" }
```
#### v-for循环对象
```
<body>
<div id="app">
    <p v-for = "(val,key,i) in user">值是：{{val}} --- 键是：{{key}} --- 索引：{{i}}</p>
</div>
<script>
    //创建一个vue的实例
    var vm = new Vue({
        el:'#app',
        data:{
            user:{
                id:1,
                name:'小猫',
                gender:'男'
            }
        },
        methods:{}
    })
</script>
</body>
```
页面效果如下：
```
值是：1 --- 键是：id --- 索引：0

值是：小猫 --- 键是：name --- 索引：1

值是：男 --- 键是：gender --- 索引：2
```
#### v-for迭代数字
```
<body>
<div id="app">
    <!-- 迭代数字，值从1开始 -->
    <p v-for="count in 10">这是第{{count}}次循环</p>
</div>
<script>
    //创建一个vue的实例
    var vm = new Vue({
        el:'#app',
        data:{
            msg:'桃之夭夭，灼灼其华'
        },
        methods:{}
    })
</script>
</body>
```
```
这是第1次循环

这是第2次循环

这是第3次循环

这是第4次循环

这是第5次循环

这是第6次循环

这是第7次循环

这是第8次循环

这是第9次循环

这是第10次循环
```
### v-for循环中key属性的使用
 v-for 循环的时候，key 属性只能使用 number获取string。
 
key 在使用的时候，必须使用 v-bind 属性绑定的形式，指定 key 的值。

在组件中，使用v-for循环的时候，或者在一些特殊情况中，如果 v-for 有问题，必须 在使用 v-for 的同时，指定 唯一的 字符串/数字 类型 :key 值。


 
```
<body>
<div id="app">
        <div>
            <label>Id:
                <input type="text" v-model = "id">
            </label>
            <label>Name:
                <input type="text" v-model="name">
            </label>
            <input type="button" value="添加" @click="add"/>
        </div>
        <p v-for = "item in list" :key ="item.id">
            <input type="checkbox"/>{{item.id}} --- {{item.name}}
        </p>
</div>
<script>
    //创建一个vue的实例
    var vm = new Vue({
        el:'#app',
        data:{
            id:'',
            name:'',
            list:[
                {id:1,name:'李斯'},
                {id:2,name:'嬴政'},
                {id:3,name:'赵高'},
                {id:4,name:'韩非子'},
                {id:5,name:'荀子'}
            ]
        },
        methods:{
            add(){
                //this.list.push({id:this.id,name:this.name})
                this.list.unshift({id:this.id,name:this.name})
            }
        }
    })
</script>
</body>
```
### v-if和v-show的使用
v-if 的特点：

每次都会重新删除或创建元素。

有较高的切换性能消耗。

v-show 的特点：

每次不会重新进行DOM的删除和创建操作，只是切换了元素的 display:none 样式。

有较高的初始渲染消耗。

**注意**

如果元素涉及到频繁的切换，最好不要使用 v-if，而是推荐使用。

如果元素可能永远也不会被显示出来被用户看到，则推荐使用 v-if。
```
<body>
<div id="app">
    <input type="button" value="toggle" @click ="toggle">
    <!-- 也可以直接写在click里面 -->
    <!--
    <input type="button" value="toggle" @click ="flag = !flag">
    -->
    <h3 v-if = "flag">用v-if控制的元素</h3>
    <h3 v-show = "flag">用v-show控制的元素</h3>
</div>
<script>
    //创建一个vue的实例
    var vm = new Vue({
        el:'#app',
        data:{
            flag:true
        },
        methods:{
            toggle(){
                this.flag = !this.flag
            }
        }
    })
</script>
</body>
```