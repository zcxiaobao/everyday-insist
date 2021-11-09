## 数据类型检测函数

```js
function myTypeof(obj) {
   return Object.prototype.toString.call(obj).slice(8, -1).toLowerCase() 
}
```