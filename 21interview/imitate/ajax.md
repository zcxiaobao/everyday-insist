## 模拟实现ajax
```js
function ajax({
    url= null,
	method = 'GET',
	dataType = 'JSON',
	async = true}){
	return new Promise((resolve, reject) => {
		let xhr = new XMLHttpRequest()
		xhr.open(method, url, async)
		xhr.responseType = dataType
		xhr.onreadystatechange = () => {
			if(!/^[23]\d{2}$/.test(xhr.status)) return;
			if(xhr.readyState === 4) {
				let result = xhr.responseText
				resolve(result)
			}
		}
		xhr.onerror = (err) => {
			reject(err)
		}
		xhr.send()
	})
}

```