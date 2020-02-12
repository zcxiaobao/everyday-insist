[原题链接](https://github.com/haizlin/fe-interview/issues/419)
### vue-router怎么重定向页面？
- 分析：重定向在`vue-router`实现比较简单，配置`redirect`
- 学习：(`redirect`配置)
```js
// redirect可以是url路径
{
   path: '/a',
   redirect: '/b'
}
// redirect可以是命名路由
{
  path: '/a',
  redirect: {name: 'b'}
}
// redirect也可以是方法
{
  path: '/b',
  redirect: to => {
    // 方法接受 目标路由 作为参数
    // return 重定向的 字符串路径/路径对象
  }
}
```
- 额外：别名`alias`
  1. `alias`与`redirect`的区别：
    + `redirect`：`/a`重定向为`/b`，当用户访问`/a`时，`URL`会更换为`/b`，然后匹配路由`/b`
    + `alias`：`/a`别名为`/b`，当用户访问`/b`时，`URL`会保持`/b`，然后匹配路由`/a`
- 扩展问题：[vue-router怎么配置404页面？](https://github.com/haizlin/fe-interview/issues/418)
- 解答：配置path: "*"
  ```js
  // *代表全匹配，因此要写在最后
  {
    path: '*',
    component: NotFoundComponent
  }
  ```