[原题链接](https://github.com/haizlin/fe-interview/issues/56)

1. typeof('abc')和 typeof 'abc'都是 string, 那么 typeof 是操作符还是函数？(2020.01.12)
   > 分析：`typeof` 在以前学习时，老师就讲过 `typeof` 是操作符，但是问题在于它还能使用函数调用的方式进行使用，那到底是不是函数那？如果不是，为什么？

- 解答：
  1. `typeof` 的返回值之一为`'function'`，如果 `typeof` 为 `function`，那么 `typeof(typeof)` 会返回`'function'`，但是经测试，上述代码浏览器会抛出错误。因此可以证明 `typeof` 并非函数。
  2. 既然 `typeof` 不是函数，那 `typeof` 后面的括号的作用是？
     > 括号的作用是进行分组而非函数的调用。—— 《javascript 高级程序设计》
  ```js
  // 举个例子
  typeof (((func))); // is equal to typeof func
  ```
