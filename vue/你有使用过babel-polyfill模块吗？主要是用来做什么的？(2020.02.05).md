[原题链接](https://github.com/haizlin/fe-interview/issues/473)
### 你有使用过babel-polyfill模块吗？主要是用来做什么的？
- 分析：前几天看别人创建的项目，默认依赖`babel-polyfill`模块，当时还疑惑为什么不是已经引用babel了吗？为什么还要单独引用一个`babel-polyfill`的模块。。。
- 解答：`babel`默认只转换新的`JavaScript`语法，而不转换新的`API`(`Object.assign`等)，所以需要使用对应的插件或者`polyfill`去模拟实现