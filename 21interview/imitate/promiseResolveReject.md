## 模拟实现promise.resolve
```js
Promise.resolve = function(value) {
    if(value instanceof Promise){
        return value
    }
    return new Promise(resolve => resolve(value))
}

```
## 模拟实现promise.reject
```js
Promise.reject = function(reason) {
    return new Promise((resolve, reject) => reject(reason))
}
```

参考链接: [大海我来了](https://juejin.cn/post/6946022649768181774)
