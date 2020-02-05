[原题链接](https://github.com/haizlin/fe-interview/issues/553)
### 怎么解决 vue 动态设置 img 的 src 不生效的问题？

- 分析：说实话这个问题我还没遇到过，但是 `vue` 切换 `img` 不都是动态改变 `src` 吗？

> 我在网上查询了一下资料，上述问题发生的情景是动态设置的 `src` 为本地图片链接(静态资源路径)，举个例子:

```js
data() {
    return {
        img_src:"../../assets/images/demo.png"
    }
}
```
- 原因：动态添加本地图片链接，`src`被当做静态资源处理，没有进行编译
- 解决方案：使用`require`引入
```js
data() {
  return {
    img_src: require("@/assents/images/demo.png")
  }
}
```