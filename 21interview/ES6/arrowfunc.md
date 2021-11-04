## 箭头函数与普通函数区别

1. 箭头函数没有this，它的this是通过作用域链查到外层作用域的this，且指向函数定义时的this而非执行时。
2. 不可以用作构造函数，不能使用new命令，否则会报错
3. 箭头函数没有arguments对象，如果要用，使用rest参数代替
4. 不可以使用yield命令，因此箭头函数不能用作Generator函数。
5. 不能用call/apply/bind修改this指向，但可以通过修改外层作用域的this来间接修改。
6. 箭头函数没有prototype属性。
