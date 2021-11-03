## 模拟实现apply
```js
Function.prototype.myApply = function (thisArg, arr) {
    thisArg = thisArg || window;
    thisArg.func = this;
    const args = []
    for (let i = 0; i<arr.length; i++) {
        args.push('arr['+ i + ']')
    }
    const result = eval('thisArg.func(' + args +')')
    delete thisArg.func;
    return result;
}

```