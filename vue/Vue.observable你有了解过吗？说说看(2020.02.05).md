### Vue.observable你有了解过吗？说说看 
- 分析：刚学`vue`时翻阅文档大致看过一眼，作用类似与`vuex`
- 学习：
  1. 使用： `Vue.observable( object )`
  2. 作用： 让一个对象可响应，vue内部会处理data函数返回的对象
  > 此`API`为`2.6`新增，低版本不兼容
  3. 实例
  ```js
  // store 
  export const store = Vue.observable({count: 0})
  export cosnt mutations = {
    setCount(count) {
      store.count = count
    }
  }

  // 使用
  import {store, mutations} from 'xxx/store.js'
  export default {
    computed: {
      count() {
        return store.count
      }
    },
    methods: {
      setCount: mutations.setCount
    }
  }
  ```
