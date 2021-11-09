## 遍历对象属性的方法

ES6 一共有 5 种方法可以遍历对象的属性。
### `for...in`

`for...in`循环遍历对象自身的和继承的可枚举属性（不含 `Symbol` 属性）。

### `Object.keys(obj)`

`Object.keys` 返回一个数组，包括对象自身的（不含继承的）所有可枚举属性（不含 `Symbol` 属性）的键名。

### `Object.getOwnPropertyNames(obj)`

`Object.getOwnPropertyNames` 返回一个数组，包含对象自身的所有属性（不含 `Symbol` 属性，但是包括不可枚举属性）的键名。

### Object.getOwnPropertySymbols(obj)

`Object.getOwnPropertySymbols` 返回一个数组，包含对象自身的所有 `Symbol` 属性的键名。

### Reflect.ownKeys(obj)

`Reflect.ownKeys` 返回一个数组，包含对象自身的（不含继承的）所有键名，不管键名是 `Symbol` 或字符串，也不管是否可枚举。

### 以上的 5 种方法遍历对象的键名，都遵守同样的属性遍历的次序规则。

+ 首先遍历所有数值键，按照数值升序排列。
+ 其次遍历所有字符串键，按照加入时间升序排列。
+ 最后遍历所有 `Symbol` 键，按照加入时间升序排列。

### for ... in 与 Object.keys 区别
`for...in`循环遍历对象自身的和**继承**的可枚举属性（不含 `Symbol` 属性），Object.keys 只遍历对象自身的（不含继承的）所有可枚举属性