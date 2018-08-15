# 双曲线工作室前端开发规范

此文档的编写目的是为了保证代码的规范性和一致性，降低维护代码的成本，提高多人协作的效率，保证页面性能得到最优。

## 基本原则

### 结构、样式、行为分离

HTML文档中只能包含HTML结构。与交互无关的样式置于样式表中，除了初始化指令外，将行为存放在脚本中。从CDN中调用库。

```html
<link rel="stylesheet" href="/css/layout.css">
<script src="https://libs.mhwco.org/dlvr/highlight/highlight.js"></script>
<script>hljs.initHighlightingOnLoad()</script>
```

### 缩进

统一使用Tab缩进。

### 编码

统一使用UTF-8编码。
为HTML和CSS文件设置编码。

```html
<meta charset="utf-8">
```

```css
@charset "utf-8"
```

### 注释
如果代码难以理解，就为代码增加注释。

为实现指定功能的且由多个部分构成的代码块的开始和结束增加注释。

```html
<!--article list start-->
<!--article list end-->
```

```css
/*grid layout start*/
/*grid layout end*/
```

```javascript
//ajax article start
//ajax article end
```

在JavaScript中，使用JSDoc规范。

```javascript
/**
 * Assign the project to an employee.
 * @param {Object} employee - The employee who is responsible for the project.
 * @param {string} employee.name - The name of the employee.
 * @param {string} employee.department - The employee's department.
 */
Project.prototype.assign = function(employee) {
    // ...
};
```

[Use JSDoc](http://usejsdoc.org/)

[JSDoc中文文档](http://www.css88.com/doc/jsdoc/index.html)

## HTML

### 标签

1. 自闭合标签无需闭合

```html
<br>
<img src="…">
<input type="text">
```

2. 可选的闭合标签，需要闭合

```html
<h1></h1>
<li></li>
```

3. 使用双引号

```html
<html lang="en">
```

4. 标签嵌套

- 嵌套标签严格遵守语义。

```html
<!--✔Recommended-->
<ul>
 <li>item</li>
</ul>

<!--✘NOT Recommended-->
<div>
 <li>item</li>
</div>
```

- 交互类元素不能互相嵌套。

```html
<!--✘NOT Recommended-->
<button><a href="#"></a></button>
```

- 内联元素只能嵌套内联元素。

```html
<!--✔Recommended-->
<strong>text</strong>

<!--✘NOT Recommended-->
<strong>
 <div>
  text
 </div>
</strong>
```

- &lt;p&gt;不能嵌套块元素

```html
<!--✘NOT Recommended-->
<p>
 <div>
  text
 </div>
</p>
```

### 语义

每一个人都要明确这个概念：不含样式表和行为的HTML是一个纯粹的语义系统。每一个HTML元素都有其语义。下面是一些常用标签及其语义。
| 标签       | 语义                         |
| ---------- | ---------------------------- |
| h1~h6      | 标题                         |
| p          | 段落                         |
| ul         | 无序列表                     |
| ol         | 有序列表                     |
| li         | 列表项                       |
| blockquote | 引用                         |
| cite       | 文献参考                     |
| strong     | 为强调内容而加粗             |
| em         | 为强调内容而倾斜             |
| del        | 为强调内容被删除而添加删除线 |
| code       | 代码                         |
| abbr       | 缩写                         |
| …          | …                            |