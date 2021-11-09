## 使用proxy实现arr负数索引访问
```js
const proxyArray = arr => {
    const length = arr.length;
    return new Proxy(arr, {
        get(target, key) {
            key = +key;
            while (key < 0) {
                key += length;
            }
            return target[key];
        }
    })
};
```