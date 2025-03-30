# Markdown 学习指南

## 导言
Markdown 是一种轻量级的标记语言，被广泛应用于书写技术文档、网页文本等。它易于阅读和编写，并且能转换为 HTML。

## 基本语法

### 标题
使用 `#` 来表示不同级别的标题：
```markdown
# 最顶层标题
## 次一级标题
```
### 加粗和斜体
加粗：**文字**

斜体：*文字*

混合：***加粗且倾斜***

### 列表
无序列表:
```markdown
- List Item 1
- List Item 2
  - Sublist item A
  - Sublist item B
```
有序列表：
```markdown
1. One
2. Two
3. Three
```

### 引用
引用块的开始符号为 `>`，例如:
```markdown
> 这是一个很长的一段引用。
> 继续更多的内容...
```

### 链接与图片
内联链接: 
```markdown
[百度](https://www.baidu.com)
```
参考式链接：
```markdown
![GitHub](http://github.com){target="_blank"}
```
在文档的底部注明参考的链接:
```markdown
(注释链接)[https://google.com]
```

## 高级用法

### 脚本标签
当需要插入特殊的功能性代码时，可以利用脚本标签：

Markdown中使用如下形式：
```markdown
<script>document.write("This is JavaScript code");</script>
```
这会在解析后生成对应的 HTML 代码。

### 代码块
显示纯文本区域时,可采用以下标记方式:
```markdown
```

在 ``` 符号前后分别写入或粘贴要显示的代码即可：
```python
def hello_world():
    print("Hello, World!")
    
hello_world()
```
这样，你就可以在 Markdown 书写过程中更好地结合 HTML 文档特性进行开发了。