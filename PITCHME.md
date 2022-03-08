---
theme: gaia
class: lead
paginate: true
backgroundColor: #fff
backgroundImage: url('https://marp.app/assets/hero-background.svg')
footer: 前端管理部 2022-03-03 
style: |
  :root {
    --color-background: red;
    --color-background-code: #ccc;
    --color-background-paginate: rgba(128, 128, 128, 0.05);
    --color-foreground: #345;
    --color-highlight: #99c;
    --color-highlight-hover: #aaf;
    --color-highlight-heading: #99c;
    --color-header: #bbb;
    --color-header-shadow: transparent;
  }
---
# **端端技术培训**
![bg left:50% 50%](./website/public/assets/logo.svg)

---
## 课程说明
![bg left:45% 45%](./website/public/assets/logo.svg)
- 课程内容: 
NodeJS+VueJS(全家桶)+ElementUI
- 课程节数:共8节
- 面向对象:面向所有开发人员
- 培训方式:PPT+支持线上线下
- 学习方式:理论+实践+作业+考试
---
## 目录
![bg left:45% 45%](./website/public/assets/logo.svg)
- 第一节 前端概述
- 第二节 VueJS介绍(开发规范)
- 第三节 Vue事件讲解
- 第四节 VueRouter讲解
- 第五节 Vuex讲解
- 第六节 Vue中8种组件通信方式
- 第七节 Vue+ElementUI实现系统增、删、查、改
- 第八节 培训测评
---
## 第一节 前端概述
---
### 1.1 前端常用地址
- 前端网:http://eui.ak1ak1.net
- 工具：https://pan.baidu.com/s/1iBtnXSLahWIUGRMr2xfFIw 
- 提取码：dyko
- [vuejs](https://vuejs.org)
- [vue-router](https://router.vuejs.org)
- [vuex](https://vuex.vuejs.org)
- [vue-devtools](https://github.com/vuejs/vue-devtools#vue-devtools)
- [vue-loader](https://vue-loader.vuejs.org)
- [awesome-vue](https://github.com/vuejs/awesome-vue)
---
### 1.2 前端包含内容
- HTML+JAVASCRIPT+CSS
- Javascript(BOM+ECMSCRIPT+DOM)
- CSS(less+scss+sass+stylus)
- Angular+React+Vue
- Webpack+Rollup+Gulp+Grunt
- ElementUI+AntDesign+iview
---
## 第二节 VueJS介绍(开发规范)

---
### 2.1 Vue版本
| Vue-cli版本 | Vue版本 |
| :---------: | :-----: |
| `npm install vue-cli -g`         |  V1.x   |
| `npm install vue-cli -g`        |  v2.x   |
| `npm install -g @vue/cli`        |  v3.x   |

---
### 2.2 Vue生命周期
| Vue1.x | Vue2.x        |     Vue3.x      | 说明                                                         |
| :----: | :------------ | :-------------: | :----------------------------------------------------------- |
|        | beforeCreate  |     setup()     | 在实例初始化之后，数据观测 (data observer) 和 event/watcher 事件配置之前执行，此时组件实例还未创建，通常用于**插件开发中执行一些初始化任务**。 |
|        | created       |     setup()     | 组件实例已经创建完成，并配置了数据观测 (data observer)，property 和方法的运算，watch/event 事件回调。但是还没有挂载DOM，此阶段可用于异步数据获取。 |

---
### 
| Vue1.x | Vue2.x        |     Vue3.x      | 说明                                                         |
| :----: | :------------ | :-------------: | :----------------------------------------------------------- |
|        | beforeMount   |                 | 在挂载开始之前被调用：相关的 render 函数首次被调用。         |
|        | mounted       |    onMounted    | 组件实例被挂载后完成，DOM已创建，此阶段可用于访问数据和DOM元素，但不会保证所有子组件都一起被挂载。如果您希望整个视图都完成渲染可以在 mounted 内部使用 vm.$nextTick |

---
### 
| Vue1.x | Vue2.x        |     Vue3.x      | 说明                                                         |
| :----: | :------------ | :-------------: | :----------------------------------------------------------- |
|        | beforeUpdate  | onBeforeUpdate  | 数据更新前调用，可用于获取更新前的状态。可在这里 手动移除已经添加的事件监听器。 |
|        | updated       |    onUpdated    | 此函数执行的时候。DOM已经更新( updated 不会保证所有的子组件也都一起被重绘。如果你希望等到整个视图都重绘完毕，可以在 updated 里使用 vm.$nextTick ) |

---
### 
| Vue1.x | Vue2.x        |     Vue3.x      | 说明                                                         |
| :----: | :------------ | :-------------: | :----------------------------------------------------------- |
|        | beforeDestroy | onBeforeUnmount | 实例销毁之前调用。在这一步，实例仍然完全可用，此时可以取消定时器和订阅事件。 |
|        | destroyed     |   onUnmounted   |                                                              |
|        | errorCaptured | onErrorCaptured |                                                              |

- 两个被替换了，其余的就是改了个名 
- 除了beforeCreate、created外其他生命周期钩子函数在服务器端渲染期间均不被调用。

---
## 第三节 Vue事件讲解

--- 
### 指令 3.1 v-text
```markdown
v-text主要用来更新textContent，可以等同于JS的text属性。
# 语法
<span v-text="msg"></span>

# 简写
<span>{{msg}}</span>
```
--- 
### 指令 3.2 v-html
双大括号的方式会将数据解释为纯文本，而非HTML。为了输出真正的HTML，可以用v-html指令。它等同于JS的innerHtml属性。
```markdown
# 语法
<div v-html="rawHtml"></div>

# 说明
这个div的内容将会替换成属性值rawHtml，直接作为HTML进行渲染。
```
---
### 指令 3.3 v-pre
v-pre主要用来跳过这个元素和它的子元素编译过程。可以用来显示原始的Mustache标签。跳过大量没有指令的节点加快编译。
```markdown
# 语法
<<div id="app">
    <span v-pre>{{message}}</span>  //这条语句不进行编译
</div>

# 结果
<span>{{message}}</span>
```
---
### 指令 3.4 v-cloak
这个指令是用来保持在元素上直到关联实例结束时进行编译。
```markdown
# 语法
<div id="app" v-cloak>
    <div>{{message}}</div>
</div>

# 在页面加载时会闪烁，先显示:
<div>{{message}}</div>

# 然后才会编译为：
<div>messag内容</div>
```
---
### 指令 3.5 v-once
v-once关联的实例，只会渲染一次。之后的重新渲染，实例极其所有的子节点将被视为静态内容跳过，这可以用于优化更新性能。
```markdown
# 语法
<span v-once>This will never change:{{msg}}</span>  //单个元素
<div v-once><h1>comment</h1><p>{{msg}}</p></div>
<my-component v-once:comment="msg"></my-component>  //组件
<ul><li v-for="i in list">{{i}}</li></ul>

# 说明：
上面的例子中，msg,list即使产生改变，也不会重新渲染。
```
---
### 指令 3.6 v-if
v-if可以实现条件渲染，Vue会根据表达式的值的真假条件来渲染元素。
```markdown
# 语法
<<a v-if="isStatus">yes</a>

# 说明：
如果属性值ok为true，则显示。否则，不会渲染这个元素。
```
---
### 指令 3.7 v-else
-else是搭配v-if使用的，它必须紧跟在v-if或者v-else-if后面，否则不起作用。
```markdown
# 语法
<a v-if="isStatus">yes</a>
<a v-else>No</a>

# 说明：
如果属性值ok为true，则显示。否则，不会渲染这个元素。
```
---
### 指令 3.8 v-else-if
v-else-if充当v-if的else-if块，可以链式的使用多次。可以更加方便的实现switch语句。
```markdown
# 语法
<div v-if="type==='A'">A</div>
<div v-else-if="type==='B'">B</div>
<div v-else-if="type==='C'">C</div>
<div v-else>Not A,B,C</div>

# 说明：
如果属性值ok为true，则显示。否则，不会渲染这个元素。
```
---
### 指令 3.9 v-show
v-else-if充当v-if的else-if块，可以链式的使用多次。可以更加方便的实现switch语句。
```markdown
# 语法
<h1 v-show="ok">hello world</h1>

# 说明：
也是用于根据条件展示元素。和v-if不同的是，如果v-if的值是false，则这个元素被销毁，不在dom中。但是v-show的元素会始终被渲染并保存在dom中，它只是简单的切换css的dispaly属性。

# 注意:
v-if有更高的切换开销
v-show有更高的初始渲染开销。
因此，如果要非常频繁的切换，则使用v-show较好；如果在运行时条件不太可能改变，则v-if较好

```
---
### 指令 3.10 v-for
用v-for指令根据遍历数组来进行渲染
```markdown
# 语法
<div v-for="(item,index) in items"></div>   //使用in，index是一个可选参数，表示当前项的索引
<div v-for="item of items"></div>   //使用of

# 注意:
当v-for和v-if同处于一个节点时，v-for的优先级比v-if更高。这意味着v-if将运行在每个v-for循环中

```
---
## 指令 3.11 v-bind
v-bind用来动态的绑定一个或者多个特性。没有参数时，可以绑定到一个包含键值对的对象。常用于动态绑定class和style。以及href等。简写为一个冒号【 ：】
```markdown
# 语法
# 对象语法
<div :class="{'is-active':isActive, 'text-danger':hasError}"></div>//  data: {isActive: true,   hasError: false}

# 数组语法

<p :class="[{'is-active':activeClass},errorClass]">12345</p>//data: {activeClass: false,errorClass: 'text-danger'}

# 直接绑定数据对象
<div :class="classObject">12345</div> // data: {classObject:{'is-active': false,'text-danger':true}}
```
---
## 指令 3.12 v-model
v-model会忽略所有表单元素的value、checked、selected特性的初始值。因为它选择Vue实例数据做为具体的值。
```markdown
# 语法
<input v-model="somebody">
# v-model修饰符
<1> .lazy 默认情况下，v-model同步输入框的值和数据。可以通过这个修饰符，转变为在change事件再同步。<input v-model.lazy="msg"> 
<2> .number 自动将用户的输入值转化为数值类型 <input v-model.number="msg">
<3> .trim 自动过滤用户输入的首尾空格 <input v-model.trim="msg">
```


---
## 3.13 v-on

```markdown
# 概念
v-on主要用来监听dom事件，以便执行一些代码块。表达式可以是一个方法名。
语法:在 vue 中，事件通过指令 v-on 进行绑定，v-on 缩写 @
<组件 v-on:事件名称="表达式" />
<组件 @事件名称="表达式" />
# 案例
<div id="app">
    <button @click="consoleLog"></button>
    <button v-on:click="consoleLog"></button>
</div>
```
---
### 3.13.1 事件修饰符
在事件函数中，我们可以通过 e.preventDefault()、e.stopPropagation() 来阻止默认行为，阻止冒泡，但是中 <u>vue</u> 中提供一些更加方便的方式来处理这些问题，这就是事件修饰符。
```markdown
.stop 阻止事件继续传播
.prevent 事件不再重载页面
.capture 使用事件捕获模式,即元素自身触发的事件先在此处处理，然后才交由内部元素进行处理
.self 只当在 event.target 是当前元素自身时触发处理函数
.once 事件将只会触发一次
.passive 告诉浏览器你不想阻止事件的默认行为
```
---
### 案例
```markdown
<!-- 阻止单击事件继续传播 -->
<a v-on:click.stop="doThis"></a>
<!-- 提交事件不再重载页面 -->
<form v-on:submit.prevent="onSubmit"></form>
<!-- 修饰符可以串联 -->
<a v-on:click.stop.prevent="doThat"></a>
<!-- 只有修饰符 -->
<form v-on:submit.prevent></form>
<!-- 添加事件监听器时使用事件捕获模式 -->
<!-- 即元素自身触发的事件先在此处处理，然后才交由内部元素进行处理 -->
<div v-on:click.capture="doThis">...</div>
<!-- 只当在 event.target 是当前元素自身时触发处理函数 -->
<!-- 即事件不是从内部元素触发的 -->
<div v-on:click.self="doThat">...</div>
<!-- 点击事件将只会触发一次 -->
<a v-on:click.once="doThis"></a>
<!-- 滚动事件的默认行为 (即滚动行为) 将会立即触发 -->
<!-- 而不会等待 `onScroll` 完成  -->
<!-- 这其中包含 `event.preventDefault()` 的情况 -->
<div v-on:scroll.passive="onScroll">...</div>
```
---
### 3.13.2  按键修饰符
vue 还提供了许多按键修饰符,用.keyCode。
```markdown
<组件 @keyup.13="fn" />
.enter
.down
.exact
```
---
### 3.13.3  原生事件
自定义组件中可以自定义一些事件，可以通过 .native 修饰符来指定监听原生中的事件，而不是组件自定义事件.
```markdown
<组件 @keyup.13="fn" />
.enter
.down
.exact
```
---
## 第四节 VueRouter讲解
⋅⋅⋅To have a line break without a paragraph, you will need to use two trailing spaces.⋅⋅
⋅⋅⋅Note that this line is separate, but within the same paragraph.⋅⋅
⋅⋅⋅(This is contrary to the typical GFM line break behaviour, where trailing spaces are not required.)
⋅⋅⋅You can have properly indented paragraphs within list items. Notice the blank line above, and the leading spaces (at least one, but we'll use three here to also align the raw Markdown).

---
## 第五节 Vuex讲解
* Unordered list can use asterisks
- Or minuses
+ Or pluses
---
## 第六节 Vue中8种组件通信方式
---
## 第七节 Vue+ElementUI实现系统增、删、查、改
---
## 第八节 培训测评
---
1. First ordered list item
2. Another item
⋅⋅* Unordered sub-list.
1. Actual numbers don't matter, just that it's a number
⋅⋅1. Ordered sub-list
4. And another item.

---
**感谢聆听！**
---