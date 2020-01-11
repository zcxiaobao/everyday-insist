[原题链接](https://github.com/haizlin/fe-interview/issues/59)

1. 什么是 FOUC？你是如何避免 FOUC 的？(2020.01.11)
   > 分析：这是一个从未听说过的概念，因此去找度娘查询了一下，再次记录一下。
   > 参考`[AricZhu]`、`[Konata9]`

- 现象：文档结构表（`HTML`）先于样式表（`CSS`）渲染，造成无样式页面内容的瞬间闪烁。
- 造成 `FOUC` 现象本质：`css` 晚于 `html` 加载
- 造成 `FOUC` 现象的常见原因：
  - 通过 `@import` 方式导入样式表
  - `style` 标签在 `body` 中
- 解决方式：把 `link` 标签将样式放在 `head` 中

2. 通过对 FOUC 的了解，发现两个类似面试问题，记录一下

- [`style`标签写在`body`前和`body`后的区别是什么？](https://github.com/haizlin/fe-interview/issues/47)
- `@import`为什么会造成`FOUC`问题？
  - 由于`@import`的加载顺序造成的，页面全部加载过后`@import`引用的`css`才会加载。
- [`css` 中`@import` 和 `link` 的区别](https://github.com/daily-interview/fe-interview/issues/26)
  > 参考`[artdong]`
  1. 属性不同：`link` 是 `html` 提供的标签，`@import` 为 `css` 的语法规则。
  2. 加载顺序问题：页面打开时，`link` 引用的 `css` 被加载，而`@import` 引用的 `css` 等页面加载完毕后最后加载。
  3. 兼容性：`@import` 是 `css2.1` 后提出，存在兼容性问题。
  4. `DOM` 控制性：`link` 支持使用 `javascript` 控制 `DOM` 改变。
