[原题链接](http://blog.poetries.top/FE-Interview-Questions/base/#_11-%E4%BB%8B%E7%BB%8D%E4%B8%80%E4%B8%8B%E6%A0%87%E5%87%86%E7%9A%84css%E7%9A%84%E7%9B%92%E5%AD%90%E6%A8%A1%E5%9E%8B%EF%BC%9F%E4%BD%8E%E7%89%88%E6%9C%ACie%E7%9A%84%E7%9B%92%E5%AD%90%E6%A8%A1%E5%9E%8B%E6%9C%89%E4%BB%80%E4%B9%88%E4%B8%8D%E5%90%8C%E7%9A%84%EF%BC%9F)

1. 介绍一下标准的 CSS 的盒子模型？低版本 IE 的盒子模型有什么不同的？
   > css 盒子模型分为两种：IE 盒子模型，标准盒子模型

- 解答：
  1. 盒模型：内容(`content`)、内边距(`padding`)、边框(`border`)、外边距(`margin`)
  2. `W3C` 标准盒子的 `width/height` 为 `content` 部分的宽高，`IE` 盒子的 `width/height` 为 `content + padding + border`。
  3. `css3` 提供 `box-sizing` 可以转换盒子模型。`border-box(IE)/content-box(W3C,默认)`
