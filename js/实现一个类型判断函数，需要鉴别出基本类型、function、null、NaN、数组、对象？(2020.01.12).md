[原题链接](https://github.com/huruji/FE-Interview/blob/master/docs/JavaScript.md#15%E5%AE%9E%E7%8E%B0%E4%B8%80%E4%B8%AA%E7%B1%BB%E5%9E%8B%E5%88%A4%E6%96%AD%E5%87%BD%E6%95%B0%E9%9C%80%E8%A6%81%E9%89%B4%E5%88%AB%E5%87%BA%E5%9F%BA%E6%9C%AC%E7%B1%BB%E5%9E%8Bfunctionnullnan%E6%95%B0%E7%BB%84%E5%AF%B9%E8%B1%A1)

1. 实现一个类型判断函数，需要鉴别出基本类型、function、null、NaN、数组、对象？(2020.01.12)
   > 分析：主要区别几个特殊类型即可，例如 null、array、普通对象返回值都为"object"，number、NaN 返回值都为"number"，isArray 和 isNaN。

- 解答：[具体测试](./cases/typeof/typeof测试.html)

```js
function type(ele) {
  if (ele === null) {
    return "null";
  }
  const eleType = typeof ele;
  if (eleType === "object") {
    return Array.isArray(ele) ? "array" : eleType;
  } else if (eleType === "number") {
    return isNaN(ele) ? "NaN" : eleType;
  } else {
    return eleType;
  }
}
```
