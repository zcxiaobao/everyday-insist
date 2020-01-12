[原题链接](https://github.com/haizlin/fe-interview/issues/1567)

1. 请解释下 NaN 表示什么呢？typeof NaN 结果是什么？(2020.01.12)

- NaN：not a number，ECMA 规定其类型为"number"，typeof NaN => "number"
- 判断一个只是否为 NaN？

```js
// NaN是一个比较特殊的值
NaN === NaN; // false
// 由于NaN与任何值都不相等，那么如何判断一个值为NaN那
// 1. 字符串判断
number + "" === "NaN";
// 2. 利用其与自身不相等
!test === test;
// 3. isNaN函数
isNaN(number);
// 4. Number.isNaN
Number.isNaN(number);
```

> isNaN 与 Number.isNaN 区别：前者会发生隐式类型转换，后者只会在值为 NaN 时返回 true。

```js
isNaN("hello world!"); // true
Number.isNaN("hello world!"); // false
```
