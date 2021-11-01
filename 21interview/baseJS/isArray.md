## 怎么判断数组
1. `ES6` 提供的新方法 `Array.isArray()`
2. 如果不存在`Array.isArray()`呢？可以借助`Object.prototype.toString.call()` 进行判断，此方式兼容性最好
```js
if (!Array.isArray) {
    Array.isArray = function(o) {
        return typeof(o) === 'object' 
               && Object.prototype.toString.call(o) === '[object Array]';
    }
}
```
3. `instanceof` 判断

判断方式
```js
// 如果为true，则arr为数组
arr instanceof Array
```
`instanceof` 判断数组类型如此之简单，为何不推荐使用那？

`instanceof` 操作符的问题在于，如果网页中存在多个 `iframe` ，那便会存在多个 `Array` 构造函数，此时判断是否是数组会存在问题。

更详细的内容可以参考博文：[JavaScript为啥不用instanceof检测数组
](https://blog.csdn.net/weixin_42467709/article/details/105302852)