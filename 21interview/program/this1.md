## 下列程序的输出结果是:
```js
function foo() {
    console.log(this.name);
}
function Foo(fn) {
    fn();
}
var obj = {
    name: 'zl',
    foo,
}
var name = 'Heternally'

Foo(obj.foo)
```
隐式绑定会有一下两种丢失：
+ 使用另一个变量作为函数别名，之后使用别名执行函数
+ 将函数作为参数传递时会被隐式赋值

发生绑定丢失的原因: 上面将 obj.foo 赋值给 foo ，就是将 foo 也指向了 obj.foo 所指向的堆内存，此后再执行 foo ，相当于直接执行的堆内存的函数，与 obj 无关，foo 为默认绑定。笼统的记，只要 fn 前面什么都没有，肯定不是隐式绑定。

**答案**
```js
Heternally
```