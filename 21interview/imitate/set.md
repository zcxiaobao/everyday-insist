## 模拟实现 set
```js
class Set {
  constructor() {
    this.items = {};
    this.size = 0;
  }

  has(element) {
    return element in this.items;
  }

  add(element) {
    if(! this.has(element)) {
      this.items[element] = element;
      this.size++;
    }
    return this;
  }

  delete(element) {
    if (this.has(element)) {
      delete this.items[element];
      this.size--;
    }
    return this;
  }

  clear() {
    this.items = {}
    this.size = 0;
  }

  values() {
    let values = [];
    for(let key in this.items) {
      if(this.items.hasOwnProperty(key)) {
        values.push(key);
      }
    }
    return values;
  }
}


```