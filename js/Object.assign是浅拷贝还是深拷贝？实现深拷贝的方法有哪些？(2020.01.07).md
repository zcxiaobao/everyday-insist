1. Object.assign 是浅拷贝还是深拷贝？实现深拷贝的方法有哪些？ (2020.01.07)
   > 分析：首先这是两个问题，Object 作为 ES6 新提供的 API，对此了解仅限于合并对象，对象同名属性覆盖，暂无法得出其内部机制为浅拷贝还是深拷贝。

- Object.assign 学习(具体可以参考 `js/case/assign`)
  - 基本使用：
    1. 对象合并，将源对象(source)的可枚举属性复制到目标对象(target)
    2. 源对象中存在同名属性，后面的覆盖前面
    3. 如果 Objec.assign 仅传入一个参数
    - 1. 参数是对象，返回该对象
    - 2. 参数不是对象，转成对象，返回
      - 2.1 无法转化成对象，例如 undefined、null，报错
    4. 如果非对象参数出现在源对象位置，无法转化成对象则会跳过
    - 1. undefined、null 在除 target 位置并非会报错
    - 2. Object.assign 只能拷贝自身属性，不能合并不可枚举的属性、继承属性
    5. Object 可以拷贝属性名为 Symbol 的属性
  - 注意点：
    1. Object.assign 为浅拷贝
    2. 对于嵌套对象，并且为同名属性，Object.assign 默认为替换，而不是添加
    3. 注意点 3：可以用来处理数组，将数组看作 {0: val1, 1: val2}
- Object.assign 为**_浅拷贝_**
- 实现深拷贝的方法

```js
// Object.assign 只能深拷贝原始属性

// 递归的方式 deepClone 具体参考 js/case/deepClone
function es5IsArray(obj) {
  // Es5 区分对象与数组的一种方法
  const isArrayStr = "[object Array]";
  return Object.prototype.toString.call(obj) === isArrayStr;
}
function deepClone(source) {
  let target;
  if (!source || typeof source !== "object") {
    return target;
  }
  target = es5IsArray(source) ? [] : {}; // 或者使用Array.isArray
  for (let key in source) {
    if (typeof source[key] !== "object") {
      target[key] = source[key];
    } else {
      target[key] = deepClone(source[key]);
    }
  }
  return target;
}

// JSON.stringfy JSON.parse 只能深拷贝能转换成JSON格式的对象，function和regExp不能使用
function deepCloneByJson(source) {
  const targetTmp = JSON.stringfy(source);
  const target = JSON.parse(targetTmp);
  return target;
}

// 借助类库的方法 例如jquery的$.extend等
```
