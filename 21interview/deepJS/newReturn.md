## 使用new调用函数，而这个函数中有return，那它return出来的是什么

**构造函数有返回值的情况：当构造函数返回值为对象时，直接返回这个对象；否则返回new创建的对象**

下面为测试部分
### 返回值为基本类型
假设构造函数返回值为一个基本类型，我们来看一下最后的返回结果：
```js
function Thin_User(name, age) {
    this.name = name;
    this.age = age;
    return 'i will keep thin forever';
}

Thin_User.prototype.eatToMuch = function () {
    console.log('i eat so much, but i\'m very thin!!!');
}

Thin_User.prototype.isThin = true;

const xiaobao = new Thin_User('zcxiaobao', 18);
console.log(xiaobao.name);   // zcxiaobao
console.log(xiaobao.age);    // 18
console.log(xiaobao.isThin); // true
// i eat so much, but i'm very thin!!!
xiaobao.eatToMuch(); 
```
最后的返回结果好像受到任何干扰，难道构造函数不会对返回值进行处理吗？
不急，我们来接着测试一下返回值为对象的情况。
### 返回值为对象
```js
function Thin_User(name, age) {
    this.name = name;
    this.age = age;
    return {
        name: name,
        age: age * 10,
        fat: true
    }
}

Thin_User.prototype.eatToMuch = function () {
    // 白日做梦吧，留下肥胖的泪水
    console.log('i eat so much, but i\'m very thin!!!');
}

Thin_User.prototype.isThin = true;

const xiaobao = new Thin_User('zcxiaobao', 18);
// Error: xiaobao.eatToMuch is not a function
xiaobao.eatToMuch();
```
当我执行eatToMuch时，控制台直接报错，没有当前函数，于是我打印了xiaobao对象：

![](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/fe2e8b6bd0f6443389fdd8173ed97a7b~tplv-k3u1fbpfcp-watermark.awebp)

发现xiaobao对象的age发生了改变，而且增加了fat属性，正好与构造函数的返回值一样。

