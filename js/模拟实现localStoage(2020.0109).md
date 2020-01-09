[原题链接](http://bigerfe.com/iq/n557)
1. 模拟实现localStorage(2020.01.09)
  > 初看到这个题，第一反应就是模拟实现localstorage，那问题便简单了，主要模拟其主要api：`setItem getItem clear`
  + localStorage有一个基本特性，传入的参数都为字符串，那参数为其他类型，会如何？
    - `undefined => "undefined"`
    - `null => "null"`
    - `{} => "[Objcet object]"`
    - `[] => ''`
    - 综上可以得出结论，`undefined null`会直接转化成字符串形式，其余类型调用`toString()`方法。
  + 初版(就在上面的基础上，初版代码应运而生，当时又沾沾自喜了，寻思考虑的应该非常全面了。。。)[参考链接](./js/cases/模拟实现一个localStroage.html)
  ```js
  const myLocalStorage = (function () {
      const storage = {};

      function toStr(val) {
        return typeof val === 'object' && !val || typeof val === 'undefined' ? val + "" : val.toString();
      }
      return {
        setItem(key, val) {
          val = toStr(val);
          key = toStr(key);
          storage[key] = val;
        },
        getItem(key) {
          key = toStr(key);
          return storage[key];
        },
        clear() {
          storage = {};
        }
      }
    }())
    // 看了大牛的代码，将自己的localStorage挂载至window
    Object.defineProperty(window, 'myStorage', {
      value: myLocalStorage
    })
  ```

+ 随着继续阅读他人的思路，遇到了直击灵魂的拷问：***localStorage的核心不是在于持久化存储和大容量吗？？？***
  > 那我上面模拟了个***锤子***
  + 分析：浏览器除了`localStorage`可以实现持久化存储，另外还有常用的`cookie，indexDB`等，因此本题设计的核心应该是利用`cookie`模拟实现
  + 终版代码
  ```js
  class Cookie {
      constructor() {}
      static getCookies() {
        return document.cookie.match(/([^;=]+)=([^;]+)/g) || [];
      }
      static setCookie(key, value, isExpired = 1) {
        var Days = 30;
        var exp = new Date();
        exp.setTime(exp.getTime() + Days * isExpired * 24 * 60 * 60 * 1000);
        document.cookie = key + "=" + encodeURIComponent(value) + ";expires=" + exp.toGMTString();
      }
    }

    const myLocalStorage2 = (function () {
      function toStr(val) {
        return typeof val === 'object' && !val || typeof val === 'undefined' ? val + "" : val.toString();
      }

      function getItem(key) {
        const cookieList = Cookie.getCookies();
        key = toStr(key);
        for (let i = 0; i < cookieList.length; i++) {
          var param = cookieList[i].match(/^\s*([^=]+)=(.+)/);
          if (param[1] === String(key)) {
            return decodeURIComponent(param[2]);
          }
        }
        return null;
      }

      function setItem(key, value) {
        Cookie.setCookie(key, value);
      }

      function removeItem(key) {
        Cookie.setCookie(key, "", -1)
      }
      return {
        getItem,
        setItem,
        removeItem
      }
    }())

  ```
