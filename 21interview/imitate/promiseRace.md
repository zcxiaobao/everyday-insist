## 模拟实现promise.race
```js
function promiseRace(promise) {
	if (!Array.isArray (promises)) {
		throw new Error ("promises must be an array!!!");
	
	}
	let resolved = false;
	return new Promise(function (resolve, reject) {
		try{
			promises.forEach(p =>
                p.then(data => {
                	if (!resolved) {
                		resolved = true;
                		resolve (data);
                	}
                })
            )
		} catch (error) {
			reject(error);
		}
	})
}

```