```md
README
```
# Vue 实例
## 创建一个 Vue 实例
```js
var vm = new Vue({
  // 选项
})
```
## 数据与方法
```js
// 我们的数据对象
var data = { a: 1 }

// 该对象被加入到一个 Vue 实例中
var vm = new Vue({
  data: data
})

// 获得这个实例上的属性
// 返回源数据中对应的字段
vm.a == data.a // => true

// 设置属性也会影响到原始数据
vm.a = 2
data.a // => 2

// ……反之亦然
data.a = 3
vm.a // => 3
```

# 模板语法
## 插值
### 文本
数据绑定最常见的形式“Mustache”语法 (双大括号) 的文本插值：
```html
<span>Message: {{ msg }}</span>
```

### 原始 HTML
双大括号会将数据解释为普通文本，而非 HTML 代码。为了输出真正的 HTML，你需要使用 v-html 指令：
```html

<p>Using mustaches: {{ rawHtml }}</p>
<p>Using v-html directive: <span v-html="rawHtml"></span></p>
```

### 特性
Mustache 语法不能作用在 HTML 特性上，遇到这种情况应该使用 v-bind 指令：
```html
<div v-bind:id="dynamicId"></div>
```
在布尔特性的情况下，它们的存在即暗示为 true，v-bind 工作起来略有不同，在这个例子中：
```html
<button v-bind:disabled="isButtonDisabled">Button</button>
```
如果 isButtonDisabled 的值是 null、undefined 或 false，则 disabled 特性甚至不会被包含在渲染出来的 <button> 元素中。

## 指令
- 指令 (Directives) 是带有 v- 前缀的特殊特性。
- 指令特性的值预期是单个 JavaScript 表达式
- 指令的职责是，当表达式的值改变时，将其产生的连带影响，响应式地作用于 DOM。

### 参数
- v-bind 指令可以用于响应式地更新 HTML 特性：
```html
<a v-bind:href="url">...</a>
 <!--href 是参数，告知 v-bind 指令将该元素的 href 特性与表达式 url 的值绑定。-->
```
- v-on 指令，它用于监听 DOM 事件：
```html
<a v-on:click="doSomething">...</a>
```

### 修饰符
- 以半角句号 . 指明的特殊后缀，用于指出一个指令应该以特殊方式绑定。
```html

<form v-on:submit.prevent="onSubmit">...</form>
<!--.prevent 修饰符告诉 v-on 指令对于触发的事件调用 event.preventDefault()：-->

```

## 缩写
Vue.js 为 v-bind 和 v-on 这两个最常用的指令，提供了特定简写：

- v-bind 缩写
```html
<!-- 完整语法 -->
<a v-bind:href="url">...</a>

<!-- 缩写 -->
<a :href="url">...</a>
```
- v-on 缩写
```html
<!-- 完整语法 -->
<a v-on:click="doSomething">...</a>

<!-- 缩写 -->
<a @click="doSomething">...</a>
```
# 计算属性和侦听器

## 计算属性
### 基础例子
```html
<div id="example">
  <p>Original message: "{{ message }}"</p>
  <p>Computed reversed message: "{{ reversedMessage }}"</p>
</div>
```
```js
var vm = new Vue({
  el: '#example',
  data: {
    message: 'Hello'
  },
  computed: {
    // 计算属性的 getter
    reversedMessage: function () {
      // `this` 指向 vm 实例
      return this.message.split('').reverse().join('')
    }
  }
})
```

