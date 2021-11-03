## 如何实现数组去重
#### 使用双重 `for` 和 `splice`
```js
function unique(arr){            
    for(var i=0; i<arr.length; i++){
        for(var j=i+1; j<arr.length; j++){
            if(arr[i]==arr[j]){         
            //第一个等同于第二个，splice方法删除第二个
                arr.splice(j,1);
                // 删除后注意回调j
                j--;
            }
        }
    }
return arr;
}
```
#### 使用 `indexOf` 或 `includes` 加新数组
```js
//使用indexof
function unique(arr) {
    var uniqueArr = []; // 新数组
    for (let i = 0; i < arr.length; i++) {
        if (uniqueArr.indexOf(arr[i]) === -1) {
            //indexof返回-1表示在新数组中不存在该元素
            uniqueArr.push(arr[i])//是新数组里没有的元素就push入
        }
    }
    return uniqueArr;
}
// 使用includes
function unique(arr) {
    var uniqueArr = []; 
    for (let i = 0; i < arr.length; i++) {
        //includes 检测数组是否有某个值
        if (!uniqueArr.includes(arr[i])) {
            uniqueArr.push(arr[i])//
        }
    }
    return uniqueArr;
}
```
#### `sort` 排序后，使用快慢指针的思想
```js
function unique(arr) {
    arr.sort((a, b) => a - b);
    var slow = 1,
        fast = 1;
    while (fast < arr.length) {
        if (arr[fast] != arr[fast - 1]) {
            arr[slow ++] = arr[fast];
        }
        ++ fast;
    }
    arr.length = slow;
    return arr;
}
```
`sort` 方法用于从小到大排序(返回一个新数组)，其参数中不带以上回调函数就会在两位数及以上时出现排序错误(如果省略，元素按照转换为的字符串的各个字符的 `Unicode` 位点进行排序。两位数会变为长度为二的字符串来计算)。
#### `ES6` 提供的 `Set` 去重
```js
function unique(arr) {
    const result = new Set(arr);
    return [...result];
    //使用扩展运算符将Set数据结构转为数组
}
```
`Set` 中的元素只会出现一次，即 `Set` 中的元素是唯一的。
#### 使用哈希表存储元素是否出现(`ES6` 提供的 `map`)
```js
function unique(arr) {
    let map = new Map();
    let uniqueArr = new Array();  // 数组用于返回结果
    for (let i = 0; i < arr.length; i++) {
      if(map.has(arr[i])) {  // 如果有该key值
        map.set(arr[i], true); 
      } else { 
        map.set(arr[i], false);   // 如果没有该key值
        uniqueArr.push(arr[i]);
      }
    } 
    return uniqueArr ;
}
```
`map` 对象保存键值对，与对象类似。但 `map` 的键可以是任意类型，对象的键只能是字符串类型。

如果数组中只有数字也可以使用普通对象作为哈希表。
#### `filter` 配合 `indexOf`
```js
function unique(arr) {
    return arr.filter(function (item, index, arr) {
        //当前元素，在原始数组中的第一个索引==当前索引值，否则返回当前元素
        //不是那么就证明是重复项，就舍弃
        return arr.indexOf(item) === index;
    })
}
```
这里有可能存在疑问，我来举个例子：
```js
const arr = [1,1,2,1,3]
arr.indexOf(arr[0]) === 0 // 1 的第一次出现
arr.indexOf(arr[1]) !== 1 // 说明前面曾经出现过1
```
#### `reduce` 配合 `includes`
```js
function unique(arr){
    let uniqueArr = arr.reduce((acc,cur)=>{
        if(!acc.includes(cur)){
            acc.push(cur);
        }
        return acc;
    },[]) // []作为回调函数的第一个参数的初始值
    return uniqueArr
}
```