---
aliases:
  - Vue
data: 2025-04-10T20:56:00
tags:
  - 步知处
  - Vue
---
# Vue

### 开发环境
### 创建项目
```cmd
npm init vue@latest
```
### 项目结构
### 基本语法
#### 模板语法
```html
<template>
    <h3>模板语法(文本插值)</h3>
    <p>{{ message0 }}</p>
    <p>{{ message1 }}</p>
    <p>{{ message2 }}</p>
    <p v-html="message2"></p>
</template>

<script>
    export default {
        data() {
            return {
                message0: '支持:单一表达式,三元表达式,',
                message1: '不支持:赋值,判断等多行表达式,',
                message2: "<a href='https://www.baidu.com/'>这是一个字符串,如果渲染html需要v-html</a>"
            }
        }
    }
</script>
```
#### 属性绑定
```html
<template>
    <h3>属性绑定</h3>
    <p class="{{ message3 }}">{{}}在html标签内不被支持</p>
    <p v-bind:id="message3" v-bind:class="message4">需要v-bind</p>
    <p v-bind:id="message5">v-bind绑定null或者undefined属性会自动移除</p>
    <p :id="message4">v-bind简写:+属性名</p>
    <p><button :disabled="message6">可以绑定布尔值</button></p>
    <p v-bind="message7">同时绑定多个值</p>
</template>

<script>
    export default {
        data() {
            return {
                message3: 'id0.0',
                message4: 'active',
                message5: null,
                message6: true,
                message7: {
                    id: 'id1',
                    class: 'active'
                }
            }
        }
    }
</script>

<style>
    .active {
        color: red;
    }
</style>
```

#### 条件渲染
```html
<template>
    <h3>条件渲染</h3>
    <p v-if="message8">v-if 子元素销毁重建 切换开销大</p>
    <p v-else>v-else</p>
    <p v-if="message9 === 'A'">A</p>
    <p v-else-if="message9 === 'B'">B</p>
    <p v-else>C</p>
    <p v-show="message8">v-show 子元素显示隐藏 初始开销大</p>
</template>

<script>
    export default {
        data() {
            return {
                message8: false,
                message9: 'A'
            }
        }
    }
</script>

```

#### 列表渲染
```html
<template>
    <h3>列表渲染</h3>
    <p v-for="item in message10">{{ item }}</p>
    <p v-for="(item, index) of message10">{{ index }}-{{ item }}</p>
    <!-- key推荐用唯一索引 不要用index -->
    <p v-for="(v, k, i) of message11" :key="i">{{ i }}-{{ k }}-{{ v }}</p>
</template>

<script>
    export default {
        data() {
            return {
                message10: ['a', 'b', 'c'],
                message11: {
                    a: '11',
                    b: '22',
                    c: '33'
                }
            }
        }
    }
</script>
```

#### 事件处理
```html
<template>
    <h3>事件处理</h3>
    <button v-on:click="message8 = !message8">v-on 绑定事件 内联{{ message8 }}</button>
    <button @click="message8 = !message8">v-on 绑定事件 内联{{ message8 }}</button>
    <button @click="m1()">v-on 绑定事件 方法</button>
    <button @click="m2('1', $event)">v-on 绑定事件 传参 方法</button>
    <button @click.stop="m1()">v-on 绑定事件 事件修饰符</button>
</template>

<script>
    export default {
        data() {
            return {
                message8: false,
            }
        },
        methods: {
            m1() {
                alert(1)

            },
            m2(a, e) {
                alert(a)
                alert(e)
            }
        }
    }
</script>
```

#### 数组监听
```html
<template>
    <h3>数组监听</h3>
    <p v-for="(item, index) of message10">{{ index }}-{{ item }}</p>
    <button @click="handleArrayOperations()">操作数据</button>
</template>
<script>
    export default {
        data() {
            return {
                message10: ['a', 'b', 'c'],
            }
        },
        methods: {
            handleArrayOperations() {
                // 修改原数组 UI自动更新
                this.message10.unshift('x') // 在数组开头添加元素
                return
                this.message10.push('d') // 在数组末尾添加元素
                this.message10.shift() // 删除数组开头元素
                this.message10.pop() // 删除数组末尾元素
                this.message10.splice(1, 1) // 删除指定位置的元素
                this.message10.splice(1, 1, 'e') // 修改指定位置的元素
                this.message10.splice(1, 0, 'e') // 在指定位置插入元素
                this.message10.splice(1, 0, 'e', 'f') // 在指定位置插入多个元素
                this.message10.sort() // 排序
                this.message10.reverse() // 反转
                // 返回新数组 UI不会自动更新
                this.message10.concat(['g', 'h']) // 合并数组
                this.message10.slice(1, 3) // 截取数组
                this.message10.filter((item) => item !== 'a') // 过滤数组
            }
        }
    }
</script>
```

#### 计算属性
```html
<template>
    <h3>计算属性</h3>
    <p>{{ c1 }}</p>
</template>

<script>
    export default {
        data() {
            return {
                message10: ['a', 'b', 'c'],
            }
        },
        computed: {
            // 计算属性 属性变化时会重新计算 相比于函数方法 性能更好 更适合复杂逻辑
            c1() {
                return this.message10.join('')
            }
        },
        methods: {
            // 函数方法 调用时会重新执行
        }
    }
</script>
```