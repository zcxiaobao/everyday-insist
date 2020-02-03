### 一道面试题让你彻底掌握JS中的EventLoop（头条）
```js
async function async1() {
    console.log('async1 start');
    await async2();
    console.log('async1 end');
}
async function async2() {
    console.log('async2');
}
console.log('script start');
setTimeout(function() {
    console.log('setTimeout');
}, 0)
async1();
new Promise(function(resolve) {
    console.log('promise1');
    resolve();
}).then(function() {
    console.log('promise2');
});
console.log('script end');
```
- 分析：关于Event Loop的题，无非就是考察同步任务、异步任务，更深一步考察macro任务、micro任务。上面这个题难点在于添加了async与await
- 解答：
  - async与await是promise的语法糖。
    - 函数开始部分 --> await 部分：Promise构造函数部分
    - await以后：then/catch
```js
// 剔除预编译过程
console.log('script start');
// 同步任务 
// 打印 ===script start===

setTimeout(function() {
    console.log('setTimeout');
}, 0)
// 定时器 异步任务 macro 压入Event Table

async1();
// Promise创建部分执行
// 执行 console.log('async1 start')
// 打印 ===async1 start===
// 执行await async2() 想当于resolve
// 打印 ===async2===
// await以后代码压入micro queue 

new Promise(function(resolve) {
    console.log('promise1');
    resolve();
}).then(function() {
    console.log('promise2');
});
// Promise创建部分执行，then压入micro queue
// 打印 ===promise1===

console.log('script end');
// 打印 ===script end===


// 同步任务执行完毕(script macro执行完毕)
// 搜查micro queue队列
// queue 先进先出

console.log('async1 end');
// 打印 ===async1 end===

console.log('promise2');
// 打印 ===promise2===

// micro执行完毕 执行下一个macro任务
setTimeout(function() {
    console.log('setTimeout');
}, 0)
// 打印 ===setTimeout===

```
- 结果： `(script start) -> (async1 start) -> (async2) -> (promise1) -> (script end) ->  (async1 end) -> (promise2) -> (setTimeout)`  