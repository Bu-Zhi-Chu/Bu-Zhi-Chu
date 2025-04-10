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
```vue
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
```vue
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
```vue
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
