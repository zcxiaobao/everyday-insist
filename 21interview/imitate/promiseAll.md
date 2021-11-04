## 实现promise.all
```js
function diPromiseAll(promises){
    return new Promise((resolve, reject)=>{
        if(!Array.isArray(promises)){
            throw new TypeError("promises must be an array")
        }
        let result = [] 
        let count = 0 
        promises.forEach((promise, index) => {
            promise.then((res)=>{
                result[index] = res
                count++
                count === promises.length && resolve(result) 
            }, (err)=>{
                reject(err)
            })
        })
    })
}

```