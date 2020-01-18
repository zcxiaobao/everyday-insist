[原题链接](https://github.com/haizlin/fe-interview/issues/1434)

1. 举例说明 atob 和 btoa 的用法(2020.01.16)
   > 分析：这是个啥？原谅我浅薄的 js 功底，我竟然完全不知道这是啥？

- 解答：查询了一下资料，参考解析答案，上述两个方法是 `base64` 同 `ascii` 编码相互转换的方法，是 `window` 上的对象.
  > `btoa：binary to ascii；(base64的编码) atob：ascii to binary;（base64的解码） 无法用于Unicode字符`

```js
// Define the string
var string = "Hello World!";

// Encode the String
var encodedString = btoa(string);
console.log(encodedString); // Outputs: "SGVsbG8gV29ybGQh"

// Decode the String
var decodedString = atob(encodedString);
console.log(decodedString); // Outputs: "Hello World!"
```
