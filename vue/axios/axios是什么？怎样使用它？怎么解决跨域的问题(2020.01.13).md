[原题链接](https://github.com/haizlin/fe-interview/issues/301)

1. axios 是什么？怎样使用它？怎么解决跨域的问题(2020.01.13)

- `Axios` 是一个基于 `promise` 的 `HTTP` 库，类似于 `ajax`。
- 以 `vue` 使用为例：

```js
// 安装axios依赖
npm install axios --save
// 建立axios.js文件夹，作为axios全局配置的主文件
export default http
// main.js 导入axios.js
import http from './axios.js'
// 挂载至vue的原型上
Vue.prototype.$http = http;
```

- 如何解决跨域问题？配置 `proxyTable` 代理

```js
// vue.config.js
proxyTable: {
  '/api': {
    target: 'xxx', // 目标接口域名
    changeOrigin: true, //是否跨域
    pathRewrite: {
      '^/api': '/api'  //重写接口
    }
  }
}

```
