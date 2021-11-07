## 构造函数，实例对象和原型对象关系
![](https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/e01951479a66457e9c326ebc3a0eb14f~tplv-k3u1fbpfcp-watermark.awebp?)

+ `add.prototype.constructor --> add`
+ `add1.__proto__ -> add.prototype`


## 构造函数，实例对象和原型对象是怎么挂载的
1. 实例对象与原型对象的关系挂载发生在 new 过程

+ MDN 中对 new 的描述: 使用 new 来构建函数，会执行如下四部操作：

1. 创建一个空的简单 JavaScript 对象（即 {} ）；
2. 为步骤1新创建的对象添加属性 __proto__ ，将该属性链接至构造函数的原型对象 ；
3. 将步骤1新创建的对象作为 this 的上下文 ；
4. 如果该函数没有返回对象，则返回 this 。

2. 构造函数与原型对象通过 constructor 属性联系起来

`Func.prototype.constructor --> Func`
