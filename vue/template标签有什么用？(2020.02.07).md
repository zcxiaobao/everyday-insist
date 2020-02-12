### `<template></template>`有什么用？
[参考`haha_ying_haha`博客](https://blog.csdn.net/u013594477/article/details/80774483)
- 学习：
  1. `html5`中的`template`标签(具体可见./cases/template.html)
    - `html5`提供的新标签，更加规范和语义化；可以把列表项放入`template`中，进行批量渲染
    > `template`元素设置了`display: none`
    ```html
    <template id="tmpl">
      <div class="title">template context</div>
    </template>
    ```
    ```js
    // js中如何获取template中的dom元素
    const tmpl = document.getElementById("tmpl")
    const content = document.content
    /*
    * tmpl.content
    * #document-fragment
    *   <div class="title">template context</div>
    */
    const title = content.querySelector('.title')
    ```
    > `content`属性获取内部`dom`支持`getElementById`、`querySelector`、`querySelectorAll`
  2. `vue`中的`template`标签
    - 条件渲染：[元素上使用`v-if`条件渲染分组](https://cn.vuejs.org/v2/guide/conditional.html#%E5%9C%A8-lt-template-gt-%E5%85%83%E7%B4%A0%E4%B8%8A%E4%BD%BF%E7%94%A8-v-if-%E6%9D%A1%E4%BB%B6%E6%B8%B2%E6%9F%93%E5%88%86%E7%BB%84)
    ```html
    <template v-if="ok">
      <h1>Title</h1>
      <p>Paragraph 1</p>
      <p>Paragraph 2</p>
    </template>
    ```
    - 条件渲染：[用`key`管理可复用的元素](https://cn.vuejs.org/v2/guide/conditional.html#%E7%94%A8-key-%E7%AE%A1%E7%90%86%E5%8F%AF%E5%A4%8D%E7%94%A8%E7%9A%84%E5%85%83%E7%B4%A0)
    ```html
    <!--这两个元素是完全独立的，不要复用它们-->
    <!--添加一个具有唯一值的key属性-->
    <template v-if="loginType === 'username'">
      <label>Username</label>
      <input placeholder="Enter your username" key="username-input">
    </template>
    <template v-else>
      <label>Email</label>
      <input placeholder="Enter your email address" key="email-input">
    </template>
    ```
    - 条件渲染：[`v-show`](https://cn.vuejs.org/v2/guide/conditional.html#v-show)
    > v-show不支持template，也不支持v-else
    - 列表渲染: [`v-for`中使用分组](https://cn.vuejs.org/v2/guide/list.html#%E5%9C%A8-lt-template-gt-%E4%B8%8A%E4%BD%BF%E7%94%A8-v-for)
    ```html
    <ul>
      <template v-for="item in list">
        <li class="base">{{item.base}}</li>
        <li class="divider"></li>
      </template>
    </ul>
    ```
    - 列表渲染：[`v-for with v-if`](https://cn.vuejs.org/v2/guide/list.html#v-for-%E4%B8%8E-v-if-%E4%B8%80%E5%90%8C%E4%BD%BF%E7%94%A8)
    > 不推荐在同一个元素上使用`v-for`和`v-if`，可以其中之一使用在`<template>`元素上
    