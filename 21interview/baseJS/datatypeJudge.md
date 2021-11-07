## 数据类型判断方式
### 你真的懂typeof吗？
1. `typeof`的作用？
   
   区分数据类型，可以返回7种数据类型：`number、string、boolean、undefined、object、function` ，以及 `ES6` 新增的 `symbol`
2. `typeof` 能正确区分数据类型吗？
   
   不能。对于原始类型，除 `null` 都可以正确判断；对于引用类型，除 `function` 外，都会返回 `"object"`
3. `typeof` 注意事项
   + `typeof` 返回值为 `string` 格式，注意类似这种考题: `typeof(typeof(undefined)) -> "string"`
   + `typeof` 未定义的变量不会报错，返回 `"undefiend"` 
   + `typeof(null) -> "object"`: 遗留已久的 `bug`
   + `typeof`无法区别数组与普通对象: `typeof([]) -> "object"`
   + `typeof(NaN) -> "number"`
### instanceof
1. `instanceof` 判断对象的原型链上是否存在构造函数的原型。只能判断引用类型。
2. `instanceof` 常用来判断 `A` 是否为 `B` 的实例

### Object.toString
最可靠的类型判断函数
```js
toString.call(()=>{})       // [object Function]
toString.call({})           // [object Object]
toString.call([])           // [object Array]
toString.call('')           // [object String]
toString.call(22)           // [object Number]
toString.call(undefined)    // [object undefined]
toString.call(null)         // [object null]
toString.call(new Date)     // [object Date]
toString.call(Math)         // [object Math]
toString.call(window)       // [object Window]
```