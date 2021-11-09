
## for ... of 遍历规则
一个数据结构只要部署了 `Symbol.iterator` 属性，就被视为具有 `iterator` 接口，就可以用 `for...of` 循环遍历它的成员。也就是说，`for...of` 循环内部调用的是数据结构的 `Symbol.iterator` 方法。

`for...of` 循环可以使用的范围包括数组、`Set` 和 `Map` 结构、某些类似数组的对象（比如`arguments`对象、`DOM NodeList` 对象）、后文的 `Generator` 对象，以及字符串。

## for ... of 可以遍历对象吗？
所以通过上面的遍历规则可知，只要对象中部署 `Symbol.iterator` 属性，就可以遍历对象；否则，不可以。

参考链接: [for ... of循环](https://es6.ruanyifeng.com/?search=%E9%81%8D%E5%8E%86&x=0&y=0#docs/iterator#for---of-%E5%BE%AA%E7%8E%AF)