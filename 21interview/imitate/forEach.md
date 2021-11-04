## 模拟实现forEach
```js
Array.prototype.myForEach = function (callbackFn) {
    // 判断this是否合法
    if (this === null || this === undefined) {
        throw new TypeError("Cannot read property 'myForEach' of null");
    }
    // 判断callbackFn是否合法
    if (Object.prototype.toString.call(callbackFn) !== "[object Function]") {
        throw new TypeError(callbackFn + ' is not a function')
    }
    // 取到执行方法的数组对象和传入的this对象
    var _arr = this, thisArg = arguments[1] || window;
    for (var i = 0; i < _arr.length; i++) {
        // 执行回调函数
        callbackFn.call(thisArg, _arr[i], i, _arr);
    }
}

```