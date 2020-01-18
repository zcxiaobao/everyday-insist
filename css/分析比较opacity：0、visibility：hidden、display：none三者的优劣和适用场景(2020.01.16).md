[原题链接](https://github.com/haizlin/fe-interview/issues/1719)

1. 分析比较 opacity: 0、visibility: hidden、display: none 三者的优劣和适用场景
   > 区别主要在是否占据空间和是否可被事件监听(看了别人的博客，我发现我真是个弟弟，对事物的认知严重不足)
   > [参考博客](https://www.cnblogs.com/nayek/p/11813741.html)

- 解答：
  - `display: none`:
    1. `DOM` 结构：浏览器不会渲染 `display` 属性为 `none` 的元素，不占据空间
    2. 事件监听：无法进行 `DOM` 事件监听
    3. 性能：动态改变此属性时会引起重排，性能较差
    4. 继承：不会被子元素继承，毕竟子类也不会被渲染
    5. `transition`：`transition` 不支持 `display`。
  - `visibility: hidden`:
    1. `DOM` 结构：元素被隐藏，但是会被渲染不会消失，占据空间
    2. 事件监听：无法进行 `DOM` 事件监听
    3. 性能：动态改变此属性时会引起重绘，性能较高
    4. 继承：会被子元素继承，子元素可以通过设置 `visibility: visible`来取消隐藏
    5. `transition`：`transition` 不支持 `visibility`
  - `opacity: 0`:
    1. `DOM` 结构：透明度为 `100%`，元素隐藏，占据空间
    2. 事件监听：可以进行 `DOM` 事件监听
    3. 性能：提升为合成层，不会触发重绘，性能较高
    4. 继承：会被子元素继承，且子元素并不能通过 `opacity: 1` 来取消隐藏
    5. `transition`：`transition` 支持 `opacity`。
