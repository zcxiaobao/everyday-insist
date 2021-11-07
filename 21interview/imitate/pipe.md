## pipe
```js
var pipe = function () {
    var args = Array.from(arguments);
    return function (val) {
        return args.reduce(function (result, func) {
            return func(result);
        }, val);
        // for (var i = 0; i < args.length; i++) {
        //     var func = args[i];
        //     val = func(val);
        // }
        // return val;
    }
}   
```