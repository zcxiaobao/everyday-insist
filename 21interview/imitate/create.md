## 实现object.create
```js
function newCreate(proto, propertiesObject) {
    if (typeof proto !== 'object' && typeof proto !== 'function') {
        throw TypeError('Object prototype may only be an Object: ' + proto)
    }
    function F() { }
    F.prototype = proto
    const o = new F()

    if (propertiesObject !== undefined) {
        Object.keys(propertiesObject).forEach(prop => {
            let desc = propertiesObject[prop]
            if (typeof desc !== 'object' || desc === null) {
                throw TypeError('Object prorotype may only be an Object: ' + desc)
            } else {
                Object.defineProperty(o, prop, desc)
            }
        })
    }

    return o
}

```
参考链接: [js 你需要了解的Object create实现](https://juejin.cn/post/7012623057118298149#heading-5)