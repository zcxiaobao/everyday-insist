[原题链接](http://blog.poetries.top/FE-Interview-Questions/base/#_37-http-response%E6%8A%A5%E6%96%87%E7%BB%93%E6%9E%84%E6%98%AF%E6%80%8E%E6%A0%B7%E7%9A%84)

1. css sprite 是什么，有什么优缺点？
   > 分析：`sprite` 是雪碧图，通常是将多个小图片集成为一张，可以减少 `http` 请求次数。布局时使用 `background-position` 配合 `background-size` 实现。

- 解答：
  1. 概念：将多个小图片拼接到一个图片中。通过 `background-position` 和 `background-size` 调节需要显示的背景。
  2. 优点：
  - 减少 `http` 请求数，提高页面加载速度
  - 增加图片信息重复度(都在一张图片中，需要使用的地方只需调整 `position` 和 `size`)，提高压缩比，减少图片大小。
  - 更换风格方便(只需在一张图片或几张图片修改颜色或者样式)
  3. 缺点：
  - 图片合并麻烦
  - 维护麻烦，修改一个图片可能需要重新布局整个图片和样式
