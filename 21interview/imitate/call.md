## 实现call
```js
Function.prototype.myCall = function (thisArg) {
    thisArg = thisArg || window;
    thisArg.func = this;
    const args = []
    for (let i = 1; i<arguments.length; i++) {
        args.push('arguments['+ i + ']')
    }
    const result = eval('thisArg.func(' + args +')')
    delete thisArg.func;
    return result;
}

```