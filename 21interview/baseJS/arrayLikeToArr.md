## 类数组如何转换为数组
### `Array.prototype.slice.call()`
```js
const arrayLike = {
    0: '111',
    1: '222',
    length: 2
}
console.log(Array.prototype.slice.call(arrayLike)) // ["1", "2"]
```
### `Array.from()`
  
`Array.from` 是 `ES6` 新增的方法，它可以将**类数组对象和可遍历(iterable)**转变为真正的数组。
```js
const arrayLike = {
    0: '1',
    1: '2',
    length: 2
}
console.log(Array.from(arrayLike)) // ["1", "2"]
```
### `(...)`展开运算符

扩展运算符调用的是遍历器接口，如果一个对象没有部署此接口就无法完成转换。

上面咱们自己写的普通类数组就无法使用...运算符。
```js
const arrayLike = {
    0: '1',
    1: '2',
    length: 2
}
// Uncaught TypeError: arrayLike is not iterable
console.log([...arrayLike]) // ["1", "2"]
```
如果部署了遍历器接口，例如 `arguments` 类数组，便可以使用扩展运算符。
```js
function fn() {
    console.log([...arguments])
}
fn(1,2,3) // [1, 2, 3]
```


