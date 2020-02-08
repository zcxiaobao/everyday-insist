[原题链接](https://github.com/haizlin/fe-interview/issues/471)
### 在vue事件中传入$event，使用e.target和e.currentTarget有什么区别？
- 分析：这其实是考察的event对象上的属性，currentTarget为事件绑定的元素，target为事件触发的元素。在事件委托时，两者区别较为明显。[测试链接](./cases/event.html)
