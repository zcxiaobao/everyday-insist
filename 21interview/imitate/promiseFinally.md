## 模拟实现 promise.finally 
```js
MyPromise.prototype.finally = function (cb) {
  return this.then(function (value) {
    return MyPromise.resolve(cb()).then(function () {
      return value
    })
  }, function (err) {
    return MyPromise.resolve(cb()).then(function () {
      throw err
    })
  })
}
```