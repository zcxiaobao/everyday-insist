## 模拟实现indexOf
```js
function indexOf(findVal, beginIndex = 0) {
if (this.length < 1 || beginIndex > findVal.length) {
    return -1;
}
if (!findVal) {
    return 0;
}
beginIndex = beginIndex <= 0 ? 0 : beginIndex;
for (let i = beginIndex; i < this.length; i++) {
    if (this[i] == findVal) return i;
}
return -1;
}
      
```