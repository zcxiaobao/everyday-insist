## instanceof原理，模拟实现
什么是instanceof？你能模拟实现一个instanceof吗？
1. `instanceof` 判断对象的原型链上是否存在构造函数的原型。只能判断引用类型。
2. `instanceof` 常用来判断 `A` 是否为 `B` 的实例

```js
// A是B的实例，返回true，否则返回false
// 判断A的原型链上是否有B的原型
A instaceof B
```
3. 模拟实现 `instanceof`
   
思想：沿原型链往上查找

```js
function instance_of(Case, Constructor) {
    // 基本数据类型返回false
    // 兼容一下函数对象
    if ((typeof(Case) != 'object' && typeof(Case) != 'function') || Case == 'null') return false;
    let CaseProto = Object.getPrototypeOf(Case);
    while (true) {
        // 查到原型链顶端，仍未查到，返回false
        if (CaseProto == null) return false;
        // 找到相同的原型
        if (CaseProto === Constructor.prototype) return true;
        CaseProto = Object.getPrototypeOf(CaseProto);
    }
}
```
