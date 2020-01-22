[原题链接](http://blog.poetries.top/FE-Interview-Questions/base/#_10-display%E6%9C%89%E5%93%AA%E4%BA%9B%E5%80%BC%EF%BC%9F%E8%AF%B4%E6%98%8E%E4%BB%96%E4%BB%AC%E7%9A%84%E4%BD%9C%E7%94%A8)

1. display 有哪些值？说明他们的作用
   > display 包含两类基础特征：外部显示模型(元素怎样参与流式布局的处理)和内部显示模型(元素内子元素的布局方式) ——MDN

- 解答：

```js
flex 弹性盒子布局
grid 网格布局
block 转换成块状元素。
inline 转换成行内元素。
none 设置元素不可见。
inline-block 象行内元素一样显示，但其内容象块类型元素一样显示。
list-item 象块类型元素一样显示，并添加样式列表标记。
table 此元素会作为块级表格来显示
inherit 规定应该从父元素继承 display 属性的值
```
