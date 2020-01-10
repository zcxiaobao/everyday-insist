[原题链接](https://github.com/haizlin/fe-interview/issues/1361)

> [借用(rede-陶)博客两张图片](https://blog.csdn.net/RedaTao/article/details/81504532)

1. 请分析如下 promise 执行的结果并解释原因([测试链接](./cases/promise/请分析如下promise执行的结果并解释原因.html))
   > 这是一道经典的关于 `Event Loop` 的面试题，可惜的是未加入一个 `microtask`，私自做主给加入了，希望作者原谅。

```js
console.log(1);
setTimeout(() => {
  console.log(2);
}, 0);
const promise = new Promise((resolve, reject) => {
  console.log(3);
  resolve();
  console.log(4);
});
promise.then(() => {
  console.log(5);
});
console.log(6);
```

- 分析：其实这个题并不算一个难题，只要能理清楚 `js` 的运行机制即可。唯一的难点在于有可能还未了解 `micro` 和 `macro`。
- 答案: `1 3 4 6 5 2`
- 解析：

  - js 任务分为同步任务和异步任务(`事件，定时器，promise，异步http等`)，而异步任务又分为 `microTask` 和 `macroTask`。
  - `microTask: process.nextTick, Promise, Object.observer`
  - `macroTask: script(全局任务)，setTimeout,setInterval`
  - 执行顺序：同步任务进入主线程，异步任务进入 `Event Queue` 等待，主线程全部执行完毕，去 `Event Queue` 取异步任务，直至 `Event Queue` 全部执行完毕。(流程见下图)
    ![avatar](/assets/images/EventLoop.png)
  - 异步任务也存在执行顺序，当 `macro` 执行完毕后，会先去 `microTask Queue` 查找是否有可执行的 `micro`，若有，先执行 `microTask Queue` 里面的 `micro` 任务，待全部执行完毕再执行下一个 `macro`。(流程见下图)
    ![avatar](/assets/images/asyncLoop.png)

- 执行过程简述
  1. `script` 宏任务执行
  2. `console.log(1)`执行 <kbd>打印 1</kbd>
  3. `setTimeout` `macro` 异步任务 => 分配至 `macroTask Queue`
  4. `promise` 执行，主体为同步任务，`console.log(3)`执行 <kbd>打印 3</kbd>
  5. `resolve` `micro` 异步任务 => 分配至 `microTask Queue`
  6. `console.log(4)` <kbd>打印 4</kbd>
  7. `promise.then` 异步任务位于 `microTask Queue`
  8. `console.log(6)` <kbd>打印 6</kbd>
  9. script 宏任务执行完毕，检查 `microTask Queue`，`promise.then` 执行 <kbd>打印 5</kbd>
  10. 执行下一个 `macroTask`，`setTimeout` 执行 <kbd>打印 2</kbd>
