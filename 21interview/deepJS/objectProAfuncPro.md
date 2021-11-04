## Object的_proto_指向什么
 
`Object` 是构造函数，所有的函数都是通过 `new Function` 创建了，因此 `Object` 相当于 `Function` 的实例，即 `Object.__proto__ --> Function.prototype`。


## Function的_proto_指向什么
`Function` 函数不通过任何东西创建，JS引擎启动时，添加到内存中。 `Function.__proto__ --> Function.prototype`



## 原型链图

![](https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/eafcee00dc21445cb9a9315fee57cb91~tplv-k3u1fbpfcp-watermark.awebp?)


参考链接: [JavaScript之彻底理解原型与原型链](https://juejin.cn/post/7018355953955241997)