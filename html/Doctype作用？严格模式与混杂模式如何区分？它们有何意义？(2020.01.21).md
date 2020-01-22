[原题链接](http://blog.poetries.top/FE-Interview-Questions/base/#_16-doctype%E4%BD%9C%E7%94%A8-%E4%B8%A5%E6%A0%BC%E6%A8%A1%E5%BC%8F%E4%B8%8E%E6%B7%B7%E6%9D%82%E6%A8%A1%E5%BC%8F%E5%A6%82%E4%BD%95%E5%8C%BA%E5%88%86%EF%BC%9F%E5%AE%83%E4%BB%AC%E6%9C%89%E4%BD%95%E6%84%8F%E4%B9%89)

1. Doctype 作用？严格模式与混杂模式如何区分？它们有何意义？

- 解答：
  1. 定义：文档类型定义(`DTD`)，声明位于文档的最前面(`html` 之前)，告知浏览器的解析器，要用什么文档类型、什么规范来解析文档。
  2. 区分：是否有标准的`DTD`
  3. 三种模式
  - 严格模式：严格模式的排版和 `JS` 运作模式是以该浏览器支持的最高标准运行。
  - 混杂模式：混杂模式的页面以宽松的向后兼容的方式显示；模拟老的浏览器的行为以防止站点无法工作。
  - 怪异模式：怪异模式则是使用浏览器自己的方式来解析执行代码。
  4. js 获取当前模式
  ```js
  document.compatMode;
  // CSS1Compat 严格模式
  // BackCompat 混杂模式
  ```
