[原题链接](http://bigerfe.com/iq/n486)

1. 为什么 let、const 声明的变量不在 window 上(2020.01.18)
   > 猜测：难道每个块级作用域都会单独建立一个类似与 `window` 的对象来存储 `let const` 创建的变量？

- 解答：[参考 `XiaoDHuang` 解答](https://github.com/XiaoDHuang/node_index/issues/11)
  > 上面的那个问题涉及到 `JavaScript` 执行系统的环境概念
  ##### 知识补充
  1. 环境
     > 所谓的环境：就是用来管理`“名字 -> 数据”`的对照表。
  - 基础环境组件：
    1. 声明环境(`Declarative Environment`)：引擎内核通过任何方式实现的`“名字 -> 数据”`的对照表。
    2. 对象环境(`Object Environment`)：`JavaScript` 的一个对象，用来“模拟/映射”成上述对照表的一个结果
       > 对象环境只为全局`(Global)、with(obj)`语句中的 `obj` 创建，其他情况下的环境都为声明环境。
  - 常见的四种环境
    1. 全局`(Global)`：符合环境(有声明环境和对象环境创建)
    2. 函数`(Function)`：声明环境
    3. 模块`(Module)`：声明环境
    4. `Eval`：声明环境
  ##### 解释
  - `let、const` 声明的变量放在 `declsEnv` 中，而 `var` 声明的变量放在 `objEnv` 中，因此 `let、const`并不会在 `window` 上面。
