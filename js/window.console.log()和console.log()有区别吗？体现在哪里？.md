[原题链接](https://github.com/haizlin/fe-interview/issues/1744)

1. window.console.log()和 console .log()有区别吗？体现在哪里？(2020.01.14)
   > 分析：本题主要考察 `js` 与 `nodejs` 区别，`js` 的全局变量为 `window`，而 `nodejs` 为 `global`。

- 解答：
  - `window.console.log` 只能在浏览器中使用
  - `console.log` 在浏览器、`Node` 等其他环境中都可以使用
