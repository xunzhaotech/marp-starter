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
### 3.5 v-once
- 概念
```markdown
语法:在 vue 中，事件通过指令 v-on 进行绑定，v-on 缩写 @
<组件 v-on:事件名称="表达式" />
<组件 @事件名称="表达式" />
```
- 案例
```vue
```
---
### 3.6 v-if
- 概念
```markdown
语法:在 vue 中，事件通过指令 v-on 进行绑定，v-on 缩写 @
<组件 v-on:事件名称="表达式" />
<组件 @事件名称="表达式" />
```
- 案例
```vue
```
---
### 3.1 事件语法定义
- 概念
```markdown
语法:在 vue 中，事件通过指令 v-on 进行绑定，v-on 缩写 @
<组件 v-on:事件名称="表达式" />
<组件 @事件名称="表达式" />
```
- 案例
```vue
```
---
### 3.2事件修饰符
在事件函数中，我们可以通过 e.preventDefault()、e.stopPropagation() 来阻止默认行为，阻止冒泡，但是中 <u>vue</u> 中提供一些更加方便的方式来处理这些问题，这就是事件修饰符。
```markdown
.stop
.prevent
.capture
.self
.once
.passive
```
- 案例
```vue
```
---
### 3.3 按键修饰符
vue 还提供了许多按键修饰符,用.keyCode。
```markdown
<组件 @keyup.13="fn" />
.enter
.down
.exact
```
- 案例
```vue
```
---
### 3.4 原生事件
自定义组件中可以自定义一些事件，可以通过 .native 修饰符来指定监听原生中的事件，而不是组件自定义事件.
```markdown
<组件 @keyup.13="fn" />
.enter
.down
.exact
```
- 案例
```vue
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