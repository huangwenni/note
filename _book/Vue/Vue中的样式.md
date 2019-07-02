- [Vue中的样式](#Vue中的样式)
	- [class](#class)
	- [style](#style)

### Vue中的样式
#### class
```
  <style>
    .red {
      color: red;
    }

    .thin {
      font-weight: 200;
    }

    .italic {
      font-style: italic;
    }

    .active {
      letter-spacing: 0.5em;
    }
  </style>
</head>
<body>
  <div id="app">
    <!-- <h1 class="red thin">我是h1</h1> -->

    <!-- 第一种使用方式，直接传递一个数组，注意： 这里的 class 需要使用  v-bind 做数据绑定 -->
    <!-- <h1 :class="['thin', 'italic']">我是h1</h1> -->

    <!-- 在数组中使用三元表达式 -->
    <!-- <h1 :class="['thin', 'italic', flag?'active':'']">我是h1</h1> -->

    <!-- 在数组中使用 对象来代替三元表达式，提高代码的可读性 -->
    <!-- <h1 :class="['thin', 'italic', {'active':flag} ]">我是h1</h1> -->
    <h1 :class="classObj">我是h1</h1>
  </div>
  <script>
    // 创建 Vue 实例，得到 ViewModel
    var vm = new Vue({
      el: '#app',
      data: {
        flag: true,
        classObj: { red: true, thin: true, italic: false, active: false }
      },
      methods: {}
    });
  </script>
</body>
```
#### style

```
<body>
<div id="app">
    <!-- 如果属性中包含- 需要加单引号 -->
    <!--
    <h1 :style="styleObj1">这是一个h1</h1>
    -->
    <!-- 添加两个 -->
    <h1 :style="[styleObj1,styleObj2]">这是一个h1</h1>
</div>
<script>
    //创建一个vue的实例
    var vm = new Vue({
        el:'#app',
        data:{
            styleObj1:{color:'red','font-weight':280},
            styleObj2:{'font-style':'italic'}
        },
        methods:{}
    })
</script>
</body>
```
