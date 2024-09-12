# ES6

## 1.1局部作用域

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312122116142.png)

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312122118279.png)

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312122120513.png)



## 1.2全局作用域

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312122121706.png)



![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312122125469.png)



## 2.1箭头函数

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312122127430.png)

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312122152439.png)

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312122151915.png)







![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312122152512.png)

```vue
<script>
    //普通函数
	function 函数名(){
        函数体
    }
    function sayHi(){
        console.log("123")
    }
    //函数表达式/匿名函数
    const fn = function(){//把函数赋给了fn
        console.log("123")
    }
    //调用
    fn()
    //箭头函数
    const fn = () => {
        console.log(123);
    }
    //调用
    fn()
    //只有一个形参的时候，可以省略小括号
    const fn = x => {
        console.log(x)
    }
    fn(1)
</script>
```



```vue
<script>
    //只有一行代码的时候，我们可以省略大括号
    const fn = x => console.log(x)
 	//只有一行代码的时候，可以省略return
    //1.1
    const fn = x => {
        return x + x
    } 
    //1.2和1.1一样
    const fn = x => x + x
    console.log(fn(1))
    //箭头函数可以直接返回一个对象
    const fn = (uname) => ({uname:uname})//因为函数包着的是大括号，函数体也是大括号，冲突了所以换成小括号
    console.log( fn("刘德华") );
</script>
```



# 1.0Vue基础语法

## 1.1创建vue实例

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312081839779.png)

```vue
<!-- Vue所管理的范围 -->
<div id="app">
  <!-- 这里将来会编写一些用于渲染的代码逻辑 -->
  <h1>{{ msg }}</h1>
  <a href="#">{{ count }}</a>
</div>

<!-- 引入的是开发版本包 - 包含完整的注释和警告 -->
<script src="https://cdn.jsdelivr.net/npm/vue@2.7.14/dist/vue.js"></script>

<script>
  // 一旦引入 VueJS核心包，在全局环境，就有了 Vue 构造函数
  const app = new Vue({
    // 通过 el 配置选择器，指定 Vue 管理的是哪个盒子
    el: '#app',
    // 通过 data 提供数据
    data: {
      msg: 'Hello 传智播客',
      count: 666
    }
  })

</script>
```

## 1.2插值表达式

> 作用：利用表达式进行插值，渲染到页面
>
> 表达式：是可以被求职的代码，JS引擎会将其计算出一个结果
>
> ==注意data的数据可以直接访问他的第一层数据，但是，第二层数据要访问对象属性一样访问，比如friend.name==

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312081903812.png)

```vue
<div id="app">
  <p>{{ nickname }}</p>
  <p>{{ nickname.toUpperCase() }}</p>
  <p>{{ nickname + '你好' }}</p>
  <p>{{ age >= 18 ? '成年' : '未成年' }}</p>
  <p>{{ friend.name }}</p>
  <p>{{ friend.desc }}</p>

  <!-- ----------------------- -->
  <!-- <p>{{ hobby }}</p> -->
  <!-- <p>{{ if }}</p> -->
  <!-- <p title="{{ nickname }}">我是p标签</p> -->
</div>

<script src="https://cdn.jsdelivr.net/npm/vue@2.7.14/dist/vue.js"></script>
<script>

  const app = new Vue({
    el: '#app',
    data: {
      nickname: 'tony',
      age: 18,
      friend: {
        name: 'jepson',
        desc: '热爱学习 Vue'
      }
    }
  })
</script>
```

## 1.3响应式

> 响应式：数据变化，试图自动更新
>
> // data中的数据，是会被添加到实例上
> // 1. 访问数据  实例.属性名
> // 2. 修改数据  实例.属性名 = 新值

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312081916356.png)



![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312081923989.png)

```vue
<div id="app">
  {{ msg }}
  {{ count }}
</div>

<script src="https://cdn.jsdelivr.net/npm/vue@2/dist/vue.js"></script>

<script>

  const app = new Vue({
    el: '#app',
    data: {
      // 响应式数据 → 数据变化了，视图自动更新
      msg: '你好，黑马',
      count: 100
    }
  })
  // data中的数据，是会被添加到实例上
  // 1. 访问数据  实例.属性名
  // 2. 修改数据  实例.属性名 = 新值

</script>
```



![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202408272129647.png)

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202408272131499.png)

## 1.4v-html

> vue指令：是 Vue 提供的带有 **v- 前缀** 的 特殊 标签**属性**。
>
> v-html:就是解析innerHTML

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312082300650.png)

```vue
//`配合模板字符串${}来插入内容，比如：`我今年${ age }岁了`
<div id="app">
        <div v-html="msg"></div>
    </div>
    <script src="../js/vue.js"></script>
    <script>
        const app = new Vue({
            el:"#app",
            data:{
                msg:`<a href="http://www.baidu.com">百度</a>`
            }
        })
    </script>
```

## 1.5v-show和v-if

> v-show:控制元素显示隐藏
>
> 语法:v-show="**表达式**"，表达式值**true显示**，**false隐藏**
>
> v-if:控制元素显示隐藏(**条件渲染**)
>
> 语法:v-show="**表达式**"，表达式值**true显示**，**false隐藏**

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312082325021.png)

```vue
<!-- 
    v-show底层原理：切换 css 的 display: none 来控制显示隐藏
    v-if  底层原理：根据 判断条件 控制元素的 创建 和 移除（条件渲染）
  -->

  <div id="app">
    <div v-show="flag" class="box">我是v-show控制的盒子</div>
    <div v-if="flag" class="box">我是v-if控制的盒子</div>
  </div>
  
  <script src="https://cdn.jsdelivr.net/npm/vue@2/dist/vue.js"></script>
  <script>
    const app = new Vue({
      el: '#app',
      data: {
        flag: false
      }
    })
  </script>
```

## 1.6v-else和v-else-if

> 辅助v-if经行判断渲染

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312082335017.png)

```vue
<div id="app">
        <p v-if="gender === 1">性别：♂ 男</p>
        <p v-else>性别：♀ 女</p>
        <hr>
        <p v-if="score >= 90">成绩评定A：奖励电脑一台</p>
        <p v-else-if="score >= 70">成绩评定B：奖励周末郊游</p>
        <p v-else-if="score >= 60">成绩评定C：奖励零食礼包</p>
        <p v-else>成绩评定D：惩罚一周不能玩手机</p>
      </div>
      
      <script src="../js/vue.js"></script>
      <script>
    
        const app = new Vue({
          el: '#app',
          data: {
            gender:2,
            score: 80
          }
        })
      </script>
```

## 1.7v-on内联语句

> 作用：注册时间 = 添加监听 + 提供处理逻辑
>
> 语法：①v-on:事件名(click) = "内联语句",②v-on = "methods中的函数名"

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312082342697.png)

```vue
	<div id="app">
        <button @mouseenter="count--">-</button>
        <span>{{count}}</span>
        <button v-on:mouseenter="count++">+</button>
      <button @click="count--">-</button>
      <span>{{count}}</span>
      <button v-on:click="count++">+</button>
    </div>
    <script src="../js/vue.js"></script>
    <script type="text/javascript">
        const app = new Vue({
            el:"#app",
            data:{
                count:100
            }
        })
    </script>
```

## 1.8v-on事件methods

> 所有methods中的函数，this都指向当前实例

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312082356269.png)

```vue
<div id="app">
        <button @click="fn">切换显示隐藏</button>
        <h1 v-show="isShow">黑马程序员</h1>
    </div>
    <script src="../js/vue.js"></script>
    <script type="text/javascript">
        const app = new Vue({
            el:"#app",
            data:{
                isShow:true
            },
            methods:{
                fn(){
                    //当前实例app = this
                    console.log(app === this)//true
                    app.isShow = !app.isShow
                    //所有methods中的函数，this都指向当前实例app
                    this.isShow = !this.isShow
                }
            }
        })
    </script>
```

## 1.9v-on调用传参

> @click="fn()",点击然后触发函数
>
> @input="fn()",输入框输入触发函数
>
> @change="fn()",下拉列表改变会触发函数
>
> @blur="fn()",失去焦点会触发函数

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312090005342.png)

```vue
<div id="app">
    <div class="box">
      <h3>小黑自动售货机</h3>
      <button @click="buy(5)">可乐5元</button>
      <button @click="buy(10)">咖啡10元</button>
    </div>
    <p>银行卡余额:{{money}}元</p>
  </div>

  <script src="../js/vue.js"></script>
  <script>
    const app = new Vue({
      el: '#app',
      data: {
        money:100
      },
      methods:{
        buy(money){
            this.money = this.money - money
        }
    }
    })
```

## 1.10v-bind

> 动态的设置html的标签属性
>
> 语法：v-bind:属性名="表达式"
>
> v-bind:src="表达式"，表达式算出来赋值给src

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312090017059.png)

```vue
<div id="app">
    <img v-bind:src="imgUrl" :title="msg" alt="">
    <img :src="imgUrl" :title="msg" alt="">
</div>
//浏览器相当于
<div id="app">
    <img src="imgUrl" title="msg" alt="">
</div>

    <script src="../js/vue.js"></script>
    <script type="text/javascript">
     new Vue({
        el:"#app",
        data:{
            imgUrl:"./imgs/10-01.png",
            msg:"hello"
        }
     })
    </script>
```

## 1.11v-for

> 基于数据循环，多次渲染整个元素
>
> v-for = "(item,index) in 数组"
>
> item每一项，index下标

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312090053580.png)

```vue
<div id="app">
        <h3>小黑水果店</h3>
        <ul>
            <li v-for="(item,index) in list">
                {{item}} - {{index}}
            </li>
        </ul>
        <ul>
            <li v-for="item in list">{{item}}</li>
         </ul>
</div>
    <script src="../js/vue.js"></script>
    <script type="text/javascript">
        new Vue({
            el: "#app",
            data: {
                list: ['西瓜', '苹果', '荔枝']
            },

        })
    </script>
```

## 1.12v-for中的key

> 给元素添加的唯一标识，便于Vue经行列表项的正确排序复用

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312090119018.png)

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312090120020.png)

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202408281041833.png)



```vue
<body>
    <div id="app">
      <ul>
       <li v-for="(item,index) in booksList" :key="item.id">
          <span>{{item.name}}</span>
          <span>{{item.author}}</span>
          <button @click="del(item.id)">删除</button>
        </li>
      </ul>
    </div>
    <script>
      const app = new Vue({
        el: '#app',
        data:{
          booksList:[
            {id:1,name:'《红楼梦》',author:'曹雪芹'},
            {id:2,name:'《红楼梦》',author:'曹雪芹'},
            {id:3,name:'《红楼梦》',author:'曹雪芹'},
            {id:4,name:'《红楼梦》',author:'曹雪芹'},
          ]
        },
        methods:{
            del(id){
              this.booksList = this.booksList.filter(item => item.id !== id)
            }
        }
      })
    </script>

</body>
```

## 1.13v-model

> 给**表单元素**（input、radio、select）使用，双向绑定数据，可以快速 **获取** 或 **设置** 表单元素内容

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312090123642.png)

```vue
<div id="app">
        账户： <input type="text" v-model="username"><br><br>
        密码： <input type="password" v-model="password"><br><br>
        <button @click="login()">登录</button>
        <button @click="reset()">重置</button>
    </div>
    <script src="../js/vue.js"></script>
    <script type="text/javascript">
        new Vue({
            el: "#app",
            data: {
                username: "",
                password: ""
            },
            methods: {
                login() {
                    console.log(this.username);
                    console.log(this.password);
                },
                reset(){
                    this.username = "";
                    this.password = "";                }
            }
        })
    </script>
```

## 1.14指令修饰符

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312091241514.png)

```vue
<div id="app">
    <h3>@keyup.enter  →  监听键盘回车事件</h3>
    <input @keyup.enter="fn" v-model="username" type="text">

    <h3>v-model修饰符 .trim .number</h3>
    姓名：<input v-model.trim="username" type="text"><br>
    年纪：<input v-model.number="age" type="text"><br>

    
    <h3>@事件名.stop     →  阻止冒泡</h3>
    <div @click="fatherFn" class="father">
      <div @click.stop="sonFn" class="son">儿子</div>
    </div>

    <h3>@事件名.prevent  →  阻止默认行为</h3>
    <a @click.prevent href="http://www.baidu.com">阻止默认行为</a>
  </div>
  <script src="https://cdn.jsdelivr.net/npm/vue@2/dist/vue.js"></script>
  <script>
    const app = new Vue({
      el: '#app',
      data: {
        username: '',
        age: '',
      },
      methods: {
        fatherFn () {
          alert('老父亲被点击了')
        },
        sonFn (e) {
          // e.stopPropagation()
          alert('儿子被点击了')
        },
        fn(){
          console.log(this.username);
        }
      }
    })
  </script>
```

## 1.15v-bind修改class

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312091256690.png)

```vue
<style>
.pink{}
.big{}
</style>
<div id="app">
    <div class="box" :class="{pink:false,big: true}">黑马程序员</div>
    <div class="box" :class="['pink','big']">黑马程序员</div>
  </div>
```

## 1.16v-bind操作style

> 语法：`:style="样式对象"`

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312091324923.png)

```vue
<div id="app">
    <div class="progress">
      <div class="inner" :style="{width: percent + '%'}">
        <span>{{percent}}%</span>
      </div>
    </div>
    <button @click="percent = 25">设置25%</button>
    <button @click="percent = 50">设置50%</button>
    <button @click="percent = 75">设置75%</button>
    <button @click="percent = 100">设置100%</button>
  </div>
  <script src="../../../../js/vue.js"></script>
  <script>
    const app = new Vue({
      el: '#app',
      data: {
        percent: 100
      }
    })
  </script>
```

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202408281424788.png)

```vue
 <style>

    .box{
      width: 200px;
      height: 200px;
      background-color: pink;
    }
  </style>
</head>
<body>

  <div id="app">

    <div class="box" :style="{width:'400px',height:'400px'}"></div>

  </div>
  <script>
    const app = new Vue({
      el: '#app',
      data:{

      },
      methods:{

      }
    })
  </script>
</body>
```



## 1.17v-model应用于其他表单元素

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312091343820.png)

```vue
<div id="app">
    <h3>小黑学习网</h3>

    姓名：
      <input type="text" v-model="username"> 
      <br><br>

    是否单身：
      <input type="checkbox" v-model="isSingle"> 
      <br><br>

    <!-- 
      前置理解：
        1. name:  给单选框加上 name 属性 可以分组 → 同一组互相会互斥
        2. value: 给单选框加上 value 属性，用于提交给后台的数据
      结合 Vue 使用 → v-model
    -->
    性别: 
      <input v-model="gender" type="radio" name="gender" value="1">男
      <input v-model="gender" type="radio" name="gender" value="2">女
      <br><br>

    <!-- 
      前置理解：
        1. option 需要设置 value 值，提交给后台
        2. select 的 value 值，关联了选中的 option 的 value 值
      结合 Vue 使用 → v-model
    -->
    所在城市:
      <select v-model="cityId">
        <option value="101">北京</option>
        <option value="102">上海</option>
        <option value="103">成都</option>
        <option value="104">南京</option>
      </select>
      <br><br>

    自我描述：
      <textarea v-model="desc"></textarea> 

    <button>立即注册</button>
  </div>
  <script src="https://cdn.jsdelivr.net/npm/vue@2/dist/vue.js"></script>
  <script>
    const app = new Vue({
      el: '#app',
      data: {
        username:"",
        isSingle:true,
        gender: "1",
        cityId:"102",
        desc: ""
      }
    })
  </script>
```

## 1.18计算属性

> 基于现有的数据，计算出来的新属性。以来的数据变化，自动重新计算
>
> arr.reduce(function(上一次值，当前值){}，初始值)
>
> num.toFix(2)保留2位小数

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312091359126.png)

 

```vue
<div id="app">
    <h3>小黑的礼物清单</h3>
    <table>
      <tr>
        <th>名字</th>
        <th>数量</th>
      </tr>
      <tr v-for="(item, index) in list" :key="item.id">
        <td>{{ item.name }}</td>
        <td>{{ item.num }}个</td>
      </tr>
    </table>

    <!-- 目标：统计求和，求得礼物总数 -->
    <p>礼物总数：{{totalCount}} 个</p>
  </div>
  <script src="https://cdn.jsdelivr.net/npm/vue@2/dist/vue.js"></script>
  <script>
    const app = new Vue({
      el: '#app',
      data: {
        // 现有的数据
        list: [
          { id: 1, name: '篮球', num: 1 },
          { id: 2, name: '玩具', num: 2 },
          { id: 3, name: '铅笔', num: 5 },
        ]
      },
      computed:{
        totalCount(){
            return this.list.reduce((sum,item) => sum + item.num,0)   
        }
      }
    })
  </script>
```

## 1.19计算属性和methods方法的区别

> computed和methods的方法一样

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312091624723.png)

## 1.21计算属性的完整写法

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312091639363.png)

```vue
<div id="app">
    姓：<input type="text" v-model="firstName"> +
    名：<input type="text" v-model="lastName"> =
    <span>{{ fullName }}</span><br><br>
    
    <button @click="changeName">改名卡</button>
  </div>
  <script src="https://cdn.jsdelivr.net/npm/vue@2/dist/vue.js"></script>
  <script>
    const app = new Vue({
      el: '#app',
      data: {
        firstName: '刘',
        lastName: '备',
      },
      methods: {
        changeName () {
          this.fullName = '黄忠'
        }
      },
      computed: {
        // 简写 → 获取，没有配置设置的逻辑
        // fullName () {
        //   return this.firstName + this.lastName
        // }

        // 完整写法 → 获取 + 设置
        fullName: {
          // (1) 当fullName计算属性，被获取求值时，执行get（有缓存，优先读缓存）
          //     会将返回值作为，求值的结果
          get () {
            return this.firstName + this.lastName
          },
          // (2) 当fullName计算属性，被修改赋值时，执行set
          //     修改的值，传递给set方法的形参
          set (value) {
            // console.log(value.slice(0, 1))          
            // console.log(value.slice(1))         
            this.firstName = value.slice(0, 1)
            this.lastName = value.slice(1)
          }
        }
      }
    })
  </script>
```

## 1.22watch监视器

> 监视数据变化，执行一些业务逻辑或异步操作
>
> 当监听的数据变化时调用执行

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312091815102.png)

```vue
<div id="app">
    <!-- 条件选择框 -->
    <div class="query">
      <span>翻译成的语言：</span>
      <select>
        <option value="italy">意大利</option>
        <option value="english">英语</option>
        <option value="german">德语</option>
      </select>
    </div>

    <!-- 翻译框 -->
    <div class="box">
      <div class="input-wrap">
        <textarea v-model="obj.words"></textarea>
        <span><i>⌨️</i>文档翻译</span>
      </div>
      <div class="output-wrap">
        <div class="transbox">{{}}</div>
      </div>
    </div>
  </div>
  <script src="https://cdn.jsdelivr.net/npm/vue@2/dist/vue.js"></script>
  <script>
    const app = new Vue({
      el: '#app',
      data: {
        words: '',
        obj: {
          words: ""
        }
      },
      // 具体讲解：(1) watch语法 (2) 具体业务实现
      watch: {
        // 该方法会在数据变化时调用执行
        // newValue新值, oldValue老值（一般不用）
        words (newValue) {
          console.log('变化了', newValue)
        },
        'obj.words'(newValue){
          console.log("变化了",newValue);
        }
      }
    })
  </script>
```

## 1.23watch监听器(完整版)

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312091837461.png)

```vue
<script>
data: {
        words: '',
        obj: {
          words: '苹果',
          lang:"italy"
        }
      },
      watch: {
        obj:{
          deep: true,
          immediate: true,
          handler(newValue){
            console.log(newValue);
          }
        }
      }
</script>
```

# 2.1生命周期的四个阶段

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312091856659.png)

## 2.2生命周期函数(钩子函数)

> cmud

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312091901845.png)

```vue
<div id="app">
    <h3>{{ title }}</h3>
    <div>
      <button @click="count--">-</button>
      <span>{{ count }}</span>
      <button @click="count++">+</button>
    </div>
  </div>
  <script src="https://cdn.jsdelivr.net/npm/vue@2/dist/vue.js"></script>
  <script>
    const app = new Vue({
      el: '#app',
      data: {
        count: 100,
        title: '计数器'
      },
      // 1. 创建阶段（准备数据）
      beforeCreate () {
        console.log('beforeCreate 响应式数据准备好之前', this.count)
      },
      created () {
        console.log('created 响应式数据准备好之后', this.count)
        // this.数据名 = 请求回来的数据
        // 可以开始发送初始化渲染的请求了
      },

      // 2. 挂载阶段（渲染模板）
      beforeMount () {
        console.log('beforeMount 模板渲染之前', document.querySelector('h3').innerHTML)
      },
      mounted () {
        console.log('mounted 模板渲染之后', document.querySelector('h3').innerHTML)
        // 可以开始操作dom了
      },

      // 3. 更新阶段(修改数据 → 更新视图)
      beforeUpdate () {
        console.log('beforeUpdate 数据修改了，视图还没更新', document.querySelector('span').innerHTML)
      },
      updated () {
        console.log('updated 数据修改了，视图已经更新', document.querySelector('span').innerHTML)
      },

      // 4. 卸载阶段
      beforeDestroy () {
        console.log('beforeDestroy, 卸载前')
        console.log('清除掉一些Vue以外的资源占用，定时器，延时器...')
      },
      destroyed () {
        console.log('destroyed，卸载后')
      }
    })
  </script>
```

# 3.1工程化开发和脚手架Vue CLI

> 创建项目 npm init vue@latest
>
> npm i下载所需要的
>
> npm run dev运行

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312091937379.png)

## 3.2项目目录和执行流程

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312091939489.png)



![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312092018870.png)

## 3.3组件化开发

> 组件化：一个页面可以拆分成一个个组件，每个组件有着自己独立的结构、样式、行为
>
> 跟组件：整个应用最上层的组件，包裹所有普通小组件

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312092024231.png)

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312092026974.png)

```vue
<template>
  <div class="App">
    <div class="box" @click="fn"></div>
  </div>
</template>

<script>
// 导出的是当前组件的配置项
// 里面可以提供 data(特殊) methods computed watch 生命周期八大钩子
export default {
  created () {
    console.log('我是created')
  },
  methods: {
    fn () {
      alert('你好')
    }
  }
}
</script>

```

## 3.4普通组件的注册使用

> 局部注册：只能在注册的组件内使用
>
> ①创建.vue文件在components
>
> ②在使用的组件内导入并注册script中import
>
> ③使用在template
>
> 全局注册：所有组件内都能使用

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312092251493.png)

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202408282234146.png)



![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202408282233211.png)



```vue
<template>
  <div class="App">
<!--      头部组件-->
    <HmHeader></HmHeader>
<!--    主体组建-->
    <Main></Main>
<!--  底部组件-->
    <HmFooter></HmFooter>
  </div>
</template>
相当于
  <div class="App">
    <div class="HmHeader"></div>
    <div class="Main"></div>
    <div class="HmFooter"></div>
  </div>
```

```vue
<template>
  <div class="App">
<!--      头部组件-->
    <HmHeader></HmHeader>
<!--    主体组建-->
    <Main></Main>
<!--  底部组件-->
    <HmFooter></HmFooter>
  </div>
  <div class="App">
    <div class="HmHeader"></div>
    <div class="Main"></div>
    <div class="HmFooter"></div>
  </div>
</template>
<script>
import HmHeader from "@/components/HmHeader.vue";
import Main from "@/components/Main.vue";
import HmFooter from "@/components/HmFooter.vue";
export default {
  components:{
    HmHeader: HmHeader,
    Main: Main,
    HmFooter: HmFooter
  }
}
</script>
<style>

.App{
  width: 600px;
  height: 700px;
  background-color: pink;
  margin: auto auto;
  padding: 20px;
}

</style>
```

## 3.5普通组件的全局注册

> 全局注册：所有组件内都能使用
>
> ①创建.vue文件(三个组成部分，template script style)
>
> ②main.js中全局注册

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312092325424.png)

```vue
vue3得这样
import {createApp} from 'vue'
import App from './App.vue'
import HmButton from "@/components/HmButton.vue";

const app = createApp(App)
app.component('HmButton', HmButton)
app.mount('#app')
```

## 3.6scoped样式

> 默认情况：写在组件中的样式会全局生效 -> 因此很容易造成多个组件之间的样式冲突问题
>
> 全局样式：默认组件中的样式会作用到全局
>
> 局部样式：可以给组件家伙是那个scoped属性，可以让样式之作用与当前组件
>
> scoped原理：
> 1.给当前组件模板的所有元素，都会添加上一个自定义属性 data-v-hash值
>
> data-v-5f6a9d56  用于区分开不通的组件
>
> 2.css选择器后面，被自动处理，添加上了属性选择器div[data-v-5f6a9d56]

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312092327075.png)

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312092348266.png)





![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202408310107372.png)



![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202408310109988.png)

## 3.7data函数

> 组件的data选项必须是一个函数 。保证每个组件实例，维护独立的一份数据对象
>
> 每次创建新的组件实例，都会新执行一次data函数，得到一个新对象
>
> 调用三次组件，也就创建了三个对象，这三个对象完全没有影响，完全不会影响到别人

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312100001138.png)

```vue
<template>

    <div id="app">
        <BaseCount></BaseCount>//调用三次，有三个对象，每个对象不会影响到其他的对象，每次初始化
        <BaseCount></BaseCount>//组件的时候，都会调用data()函数，相当于有三个data()函数
        <BaseCount></BaseCount>
    </div>
</template>
<script>
import BaseCount from './components/BaseCount.vue'
export default {
    name:"App",
    components:{
        'BaseCount':BaseCount
    }
}
</script> 

<script>
export default{
    //data必须是一个函数 保证每个组件实例，维护独立的数据对象
    data(){
        return{
            count: 999
        }
    }
}
</script>
```

## 3.8组件通信

> 组件通信：组件与组件之间的数据传递
>
> 组件的数据是独立的，无法直接访问其他组件的数据

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312100009780.png)

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312100010720.png)

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312100011866.png)

### 3.8.1父传子

> 父中给子添加属性传值②子props接收③使用

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312100013306.png)

### 3.8.2子传父

> 子this.$emit发送消息②父中给子添加消息监听③父中实现处理函数

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312100137247.png)

## 3.9prop

> prop：组件上组测的一些自定义属性，向子组件传递数据

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312100148652.png)

### 3.9.1props检验

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312100206616.png)

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312100204800.png)

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312100214784.png)

## 3.10prop、data和单项数据流

> 共同点：都可以给组件提供数据
>
> 区别：
>
> data的数据是**自己**的 -> 随便改
>
> prop的数据外部的 -> 不能直接改，要遵循**单项数据流**

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312100235446.png)

## 3.11v-model原理

> v-model本质上是一个语法糖(语法的简写)。
>
> 作用：提供数据的双向绑定
>
> ①数据变，视图跟着变：value
>
> ②视图变，数据跟着变@input
>
> console.log($event.target.value);//就是拿到输入框的值

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312101228130.png)

```vue
<template>
  <div>
    <!-- <input v-model="msg1" type="text"><br><br> -->
    <input v-model="msg1" type="text"><br>
    <input :value="msg2" @input="msg2 = $event.target.value" type="text"><br>
    //:value="msg2"就是在vue中修改data中的msg2的值会自动跟新页面上的值
    //@input="msg2 = $event.target.value"就是拿到输入框的值然后赋值给msg2修改data中的值
  </div>
</template>

<script>

export default {

  data() {
    return {
      msg1: "",
      msg2: ""
    }
  },
  methods: {
    inputFn(event) {
      console.log($event.target.value);//就是拿到输入框的
    }
  }
}
</script>

```

## 3.12表单类组件封装

> **父传子**：数据应该是父组件props传递过来的，v-model拆解绑定数据
>
> **子传父**：监听输入，子传父传值给父组件修改

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312101446952.png)



![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312101511683.png)

## 3.12.1简化代码

> vue3不一样，它绑定的属性:modelValue，事件是@update:modelValue

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202408312142002.png)



### 3.12.2target

> **event.target： 指的是真正触发事件的那个元素**

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202408312113289.png)

```css
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Title</title>
  <script src=""></script>
  <script src="./../vue.js"></script>
</head>
<body>

<div id="app">
  <button @click="clickFn">点击</button>
  <br>
  <input type="text" @click="clickFn" value="输入名字">
</div>

<script>

      const app = new Vue({
        el: '#app',
        data:{
        },
        methods:{
          clickFn(){
            console.log(event.target)
          }
        }
      })

</script>

</body>
</html>
```

## 3.13v-model简化组件代码

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312101515288.png)

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312101532547.png)

## 3.14.sync修饰符

> 作用：可以实现子组件和父组件数据的双向绑定
>
> 特点：prop属性名，可以自定义，非固定为value

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312101552994.png)

## 3.15ref和$refs

> 作用：利用ref和$refs可以用于获取dom元素，或组件实例
>
> 特点：查找范围->当前组件内(更精确稳定)

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312101649982.png)

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312101703990.png)

## 3.16父组件调用子组件的方法

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312101704737.png)

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312101729894.png)

```vue
<template>

    <div class="app">
      <Son ref="baseForm"></Son>
      <button @click="handleGet">获取数据</button>
      <button @click="handleReset ">重置数据</button>
    </div>

</template>
<script>
import Son from "@/components/Son.vue";

export default {
  data(){
    return{

    }
  },
  components:{
    Son
  },
  methods:{
    handleGet(){
      console.log(this.$refs.baseForm.getValues())
    },
    handleReset(){
      this.$refs.baseForm.resetValues()
    },
  }
}
</script>
<style scoped>

</style>
```

```vue
<template>
  <form action="">
    账号:<input type="text" v-model="account"> <br> <br>
    密码: <input type="text" v-model="password">
  </form>
</template>
<script>
export default {
  data(){
    return{
      account: '',
      password: '',
    }
  },
  methods:{
    getValues(){
      return{
        account: this.account,
        password: this.password,
      }
    },
    resetValues(){
      this.account = ''
      this.password = ''
    }

  }
}
</script>

<style>

</style>
```

## 3.16Vue异步更新、$nextTick

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312101739123.png)

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312101742499.png)

```vue
<template>
    <div class="app">

        <div v-if="isShowEdit">
            <input type="text" v-model="editValue" ref="inp">
            <button>确认</button>
        </div>
        <div v-else>
            <span>{{ title }}</span>
            <button @click="handleEdit">编辑</button>
        </div>
    </div>
</template>
  
<script>

export default {
    data() {
        return {
            title: "大标题",
            editValue: "",
            isShowEdit: false
        }
    },
    methods: {
        handleEdit() {
            //1.显示输入框(异步dom更新)
            this.isShowEdit = true
            //2.让输入框获取焦点($nextTick等dom更新完，立刻执行准备的函数体)
            this.$nextTick(() => {
                this.$refs.inp.focus()
            })
        }
    },
</script>    
```

# 4.1自定义指令

> 自定义指令：自己定义的指令，可以封装一些dom操作，扩展额功能
>
> vue3中把inserted改成mounted
>
> inserted指的是当指令所绑定的元素添加到页面当中的时候自动调用

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312101750655.png)

```vue
<script>
const app = createApp({})
//全局注册指令
app.directive('focus', {
    //intered会在指令所在的元素，被插入到页面中时触发
    Intered(el) {
        //el就是指令所绑定的元素
        console.log(el);
        el.focus()
    }
})
//局部注册指令    
directives: {
    //指令名：指令的配置项
    focus: {
      mounted(el) {
        el.focus()
      },
    }
  }      
  
</script>
```

## 4.2自定义指令-指令的值

> vue3中，inserted改成mounted，update改成updated

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312102119289.png)

```vue
<template>
  <div>
    <h1 v-color="color1">指令的值</h1>
    <h1 v-color="color2">指令的值</h1>
  </div>
</template>

<script>
export default {
  data(){
    return{
        color1: 'red',
        color2: 'green'
    }
  },
  directives:{
    color:{
        //1.mounted提供的是元素被添加到页面中时的逻辑
      mounted(el,binding) {
        // console.log(el,binding.value);
        //binding.value 就是指令的值
        el.style.color = binding.value
      },
        //2.updated指令的值修改的时候触发，提供值变化后更新
      updated(el,binding){
        el.style.color = binding.value
      }
    }
  }

}
</script>
```

## 4.3v-loading指令封装

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312102123520.png)

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312102125061.png)

## 4.3插槽

> 作用：让组件内部的一些结构支持自定义

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312102139418.png)

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312102140549.png)

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312102146277.png)

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312102144859.png)

## 4.3.1插槽-具名插槽

> v-slot:插槽名可以简化成#插槽名

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312102150290.png)

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312102201949.png)

## 4.3.2插槽-作用域插槽

> 作用域插槽：定义slot插槽的同时，是可以传值的。给插槽上可以绑定数据，将来使用组件时可以用

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312102205714.png)

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312102206785.png)

# 5.1单页应用程序

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312102221551.png)

## 5.2路由

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312102223789.png)

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312102224680.png)

## 5.3vueRouter

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312102225684.png)

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312102227071.png)

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312102239488.png)

## 5.4路由的封装抽离

> @相当于src目录,从src目录出发找组件
>
> 绝对路径：@/xxx

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312110001778.png)

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312110007344.png)

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312111713046.png)



## 5.5router-link实现高亮

> router-link提供的全局组件，用于替换a标签
>
> router-link自动给当前导航添加了两个高亮类名

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312110136283.png)

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312110152038.png)



![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312110155175.png)

## 5.6.1声明式导航跳转传参-查询参数传参

> 目标：在跳转路由时，经行传值

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312111503037.png)

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312111644992.png)

5.6.2声明式导航跳转传参-动态路由参数传参

> 动态路由传参：
>
> ①配置动态路由
>
> ②配置导航连接
>
> ③对应页面组件结束传递过来的值

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312111715206.png)

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312111720640.png)

## 5.6.2两种传参的区别

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312111721014.png)

## 5.6.3动态路由参数可选符

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312111723153.png)

## 5.7Vue路由-重定向

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312111725403.png)

## 5.8Vue路由-404

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312111727660.png)

## 5.9Vue路由-模式设置

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312111734364.png)

# 6.1Vue3创建项目

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312111746867.png)

```vue
创建项目
npm create vue@latest
npm init vue@latest
```



## 6.2Vue3的项目目录

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312111747648.png)

# 7.1组合式API-setup

> 1.执行实际，比beforeCreate还要早
>
> 2.setup函数中，获取不到this(this是undefined)
>
> 3.数据和函数，需要在setup最后return，才能模板应用
>
> 4.通过setup语法糖简化代码

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312111756991.png)

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312111800423.png)

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312111801736.png)

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312111807146.png)

## 7.2reacive()

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312111811616.png)

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312111819777.png)

## 7.3ref()

> ref: 接收简单类型 或 复杂类型，返回一个响应式的对象
>
> ==本质：是在原有传入数据的基础上，外层包了一层对象，包成了复杂类型底层，包成复杂类型之后，再借助 reactive 实现的响应式==
>
> 注意点：
>
> 1. 脚本中访问数据，需要通过 .value
>
> 2. 在template中，.value不需要加 (帮我们扒了一层)

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312111819711.png)

## 7.4computed

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312111831215.png)

```vue
<script setup>
import { ref,computed } from 'vue'
const list = ref([1, 2, 3, 4, 5, 6, 7, 8])

// console.log(list);
// console.log(list.value);

const computedList = computed(()=>{
  return list.value.filter(item => item > 2)
})
const changeFn = ()=>{
  list.value.push(666)
}
</script>

<template>
  <div>{{ list }}</div>
  <div>{{ computedList }}</div>
  <button @click="changeFn">修改</button>
</template>

<style></style>
```

## 7.5watch函数

> 

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312112205941.png)

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312112206147.png)



![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312112222668.png)

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312112222747.png)

```vue
<script setup>
import { ref, watch } from 'vue'
const count = ref(0)
const nickname = ref('张三')

const changeCount = () => {
  count.value++
}
const changeNickname = () => {
  nickname.value = '李四'
}

// 1. 监视单个数据的变化
//    watch(ref对象, (newValue, oldValue) => { ... })
// watch(count, (newValue, oldValue) => {
//   console.log(newValue, oldValue)
// })

// 2. 监视多个数据的变化
//    watch([ref对象1, ref对象2], (newArr, oldArr) => { ... })
// watch([count, nickname], (newArr, oldArr) => {
//   console.log(newArr, oldArr)
// })

// 3. immediate 立刻执行
// watch(count, (newValue, oldValue) => {
//   console.log(newValue, oldValue)
// }, {
//   immediate: true
// })
// --------------------------------------------
// 4. deep 深度监视, 默认 watch 进行的是 浅层监视
//    const ref1 = ref(简单类型) 可以直接监视
//    const ref2 = ref(复杂类型) 监视不到复杂类型内部数据的变化
const userInfo = ref({
  name: 'zs',
  age: 18
})
const setUserInfo = () => {
  // 修改了 userInfo.value 修改了对象的地址，才能监视到
  // userInfo.value = { name: 'ls', age: 50 }
  userInfo.value.age++
}

// deep 深度监视
// watch(userInfo, (newValue) => {
//   console.log(newValue)
// }, {
//   deep: true
// })

// 5. 对于对象中的单个属性，进行监视
watch(() => userInfo.value.age, (newValue, oldValue) => {
  console.log(newValue, oldValue)
})
</script>

<template>
  <div>{{ count }}</div>
  <button @click="changeCount">改数字</button>
  <div>{{ nickname }}</div>
  <button @click="changeNickname">改昵称</button>
  <div>-----------------------</div>
  <div>{{ userInfo }}</div>
  <button @click="setUserInfo">修改userInfo</button>
</template>
```

## 7.6生命周期函数

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312112230553.png)

```vue
<script setup>
import { onMounted } from 'vue';

// beforeCreate 和 created 的相关代码
// 一律放在 setup 中执行

const getList = () => {
  setTimeout(() => {
    console.log('发送请求，获取数据')
  }, 2000)
}
// 一进入页面的请求
getList()

// 如果有些代码需要在mounted生命周期中执行
onMounted(() => {
  console.log('mounted生命周期函数 - 逻辑1')
})

// 写成函数的调用方式，可以调用多次，并不会冲突，而是按照顺序依次执行
onMounted(() => {
  console.log('mounted生命周期函数 - 逻辑2')
})

</script>

<template>
  <div></div>
</template>
```

## 7.7组合式API下的父传子

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312112242503.png)

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312112313643.png)

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312112315775.png)

## 7.8组合式API下的子传父

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312112318597.png)

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312112350143.png)

## 7.9模板引用

> vue3组件引入就能在html代码区显示了

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312112352385.png)

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312120000279.png)

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312121504988.png)

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312121505232.png)

## 7.10provide和inject

> 跨层级组件通信

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312121507016.png)

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312121508032.png)

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312121651586.png)

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312121655532.png)

## 7.11defineOptions

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312121658240.png)

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312121659555.png)

## 7.12defineModel

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312122038631.png)

# 8.1Pinia

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202312122049665.png)

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/20231212205038.png)

# 9.0ajax

> 引入axios.js : https://cdn.jsdelivr.net/npm/axios/dist/axios.min.js

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202409011521170.png)

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202409011522149.png)

```css
<!doctype html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport"
        content="width=device-width, user-scalable=no, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title>Document</title>
</head>
<body>
<script src="https://cdn.jsdelivr.net/npm/axios/dist/axios.min.js"></script>
<script>
  axios({
    url:'http://hmajax.itheima.net/api/province'
  }).then(result =>{
    console.log(result)
    document.write(result.data.list)
  })
</script>
</body>
</html>
```

## 9.1查询参数

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202409011531454.png)

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202409011532346.png)

```css
<!doctype html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport"
        content="width=device-width, user-scalable=no, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title>Document</title>
</head>
<body>

<script src="https://cdn.jsdelivr.net/npm/axios/dist/axios.min.js"></script>
<script>
  axios({
    url: 'http://hmajax.itheima.net/api/city',
    params: {
      pname: '江苏省'
    }
  }).then(result => {
    console.log(result.data.list)
  })
</script>

</body>
</html>
```

## 9.2案例

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202409011542471.png)

## 9.3数据提交

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202409011544548.png)

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202409011544848.png)

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202409011545604.png)

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202409011546895.png)

```css
<!doctype html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport"
        content="width=device-width, user-scalable=no, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title>Document</title>
</head>
<body>

<button class="btn">注册用户</button>

<script src="https://cdn.jsdelivr.net/npm/axios/dist/axios.min.js"></script>
<script>

  document.querySelector('.btn').addEventListener('click',()=>{
    axios({
      url:'http://hmajax.itheima.net/api/register',
      method:'post',
      data:{
        username:'itheima123222',
        password:'123456'
      }
    }).then(result => {
      console.log(result)
    })
  })
</script>

</body>
</html>
```

## 9.4axios错误处理

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202409011553287.png)

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202409011554031.png)

```css
<!doctype html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport"
        content="width=device-width, user-scalable=no, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title>Document</title>
</head>
<body>

<button class="btn">注册用户</button>

<script src="https://cdn.jsdelivr.net/npm/axios/dist/axios.min.js"></script>
<script>

  document.querySelector('.btn').addEventListener('click',()=>{
    axios({
      url:'http://hmajax.itheima.net/api/register',
      method:'post',
      data:{
        username:'itheima123222',
        password:'123456'
      }
    }).then(result => {
      console.log(result)
    }).catch(error =>{
      console.log(error.response.data.message)
      alert(error.response.data.message)
    })
  })
</script>

</body>
</html>
```

## 9.5接口文档

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202409011600915.png)

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202409011604481.png)

# 10.0同步和异步

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202409021106502.png)



## ![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202409021108960.png)10.1回调函数地狱

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202409021129350.png)

## 10.2async和await

> 在函数前面声明async之后就变成了异步函数
>
> await会暂停函数继续往下执行，要在原地等待后边异步函数成功结果回来，而且会把成功的结果提取在原地，然后赋予给左边的变量，然后继续向下
>
> await会阻止异步函数内代码继续执行，原地等待结果

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202409021136029.png)

```css
<!doctype html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport"
        content="width=device-width, user-scalable=no, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title>Document</title>
</head>
<body>


<script src="https://cdn.jsdelivr.net/npm/axios/dist/axios.min.js"></script>
<script>
  async function getData(){
    const pObj = await axios({url:'http://hmajax.itheima.net/api/province'})
    const pname = pObj.data.list[0]//获取省份名字
    const cObj = await axios({url:'http://hmajax.itheima.net/api/city',params:{pname}})
    const cname = cObj.data.list[0]
    const aObj = await axios({url:'http://hmajax.itheima.net/api/area',params:{pname,cname}})
    const aname = aObj.data.list[0]
  }
  getData()
</script>

</body>
</html>
```

## 10.3捕获错误

> 如果try里某行代码报错后，try中剩余的代码不会继续执行了

![](https://raw.githubusercontent.com/fightingwithmee/vue/main/img/202409021146336.png)

```css
<!doctype html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport"
        content="width=device-width, user-scalable=no, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title>Document</title>
</head>
<body>


<script src="https://cdn.jsdelivr.net/npm/axios/dist/axios.min.js"></script>
<script>
  async function getData() {
    try {
      const pObj = await axios({url: 'http://hmajax.itheima.net/api/province'})
      const pname = pObj.data.list[0]//获取省份名字
      const cObj = await axios({url: 'http://hmajax.itheima.net/api/city', params: {pname}})
      const cname = cObj.data.list[0]
      const aObj = await axios({url: 'http://hmajax.itheima.net/api/area1', params: {pname, cname}})
      const aname = aObj.data.list[0]
    } catch (error) {
      console.dir(error)
    }
  }

  getData()
</script>

</body>
</html>
```

