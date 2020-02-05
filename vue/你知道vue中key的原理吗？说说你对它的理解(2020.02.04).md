[你知道vue中key的原理吗？说说你对它的理解](https://github.com/haizlin/fe-interview/issues/545)
### 你知道vue中key的原理吗？说说你对它的理解
- 作用：key的作用主要是为了更高效的更新虚拟DOM
> `key`值的唯一性，能让`diff`算法更快的找到需要更新的`DOM`，需要注意的是，`key`值要唯一，要不会出现很隐蔽性的更新问题。另外，尽量不要使用`index`作为`key`值