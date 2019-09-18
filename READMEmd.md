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



