## typeof 与 instanceof 的区别

typeof与instanceof都是判断数据类型的方法，区别如下：

1. typeof会返回一个变量的基本类型，instanceof返回的是一个布尔值
2. instanceof 可以准确地判断复杂引用数据类型，但是不能正确判断基础数据类型
3. 而 typeof 也存在弊端，它虽然可以判断基础数据类型（null 除外），但是引用数据类型中，除了 function 类型以外，其他的也无法判断

> 通用检测数据类型，可以采用Object.prototype.toString，调用该方法，统一返回格式“[object Xxx]” 的字符串
