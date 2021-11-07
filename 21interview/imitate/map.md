## 模拟实现 map
```js
function defaultToString(key) {
  if(key === null) {
    return 'NULL';
  } else if (key === undefined) {
    return 'UNDEFINED'
  } else if (Object.prototype.toString.call(key) === '[object Object]' || Object.prototype.toString.call(key) === '[object Array]') {
    return JSON.stringify(key);
  }
  return key.toString();
}

class Map {
  constructor() {
    this.items = {};
    this.size = 0;
  }

  set(key, value) {
    if(!this.has(key)) {
      this.items[defaultToString(key)] = value;
      this.size++;
    }
    return this;
  }

  get(key) {
    return this.items[defaultToString(key)];
  }

  has(key) {
    return this.items[defaultToString(key)] !== undefined;
  }

  delete(key) {
    if (this.has(key)) {
      delete this.items[key];
      this.size--;
    }
    return this;
  }

  clear() {
    this.items = {}
    this.size = 0;
  }

  keys() {
    let keys = [];
    for(let key in this.items) {
      if(this.has(key)) {
        keys.push(key)
      }
    }
    return keys;
  }

  values() {
    let values = [];
    for(let key in this.items) {
      if(this.has(key)) {
        values.push(this.items[key]);
      }
    }
    return values;
  }
}


```