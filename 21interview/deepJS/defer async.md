### script标签的defer和async属性有什么区别
MDN关于defer和async属性的说明如下：
1. 不设置async和defer属性， 那么脚本会同步下载并执行， 阻塞后续dom的渲染
2.  设置了defer属性。脚本异步加载，加载完后，在触发domContentLoaded事件之前执行。
3.  设置了async属性。脚本异步加载， 加载完后，立即执行，并阻塞后续dom渲染。不影响domContentLoaded事件的触发