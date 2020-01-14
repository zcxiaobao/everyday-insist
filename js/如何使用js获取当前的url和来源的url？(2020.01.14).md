[原题链接](https://github.com/haizlin/fe-interview/issues/1478)

1. 如何使用 js 获取当前的 url 和来源的 url？(2020.01.14)
   > 分析：这个问题比较简单，`location` 中记录了当前页面的 `url` 信息，`document.referrer` 记录了来源 `url`。

- 解答：`location.href` 和 `document.referrer`
