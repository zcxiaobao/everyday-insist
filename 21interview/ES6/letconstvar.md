## let const var 区别
### var
1. 存在变量提升
2. 可以重复声明
3. 在函数中使用var声明变量的时候，该变量是局部的
   
### let
1. 不存在变量提升，let声明变量前，该变量不能使用（暂时性死区）
2. let命令所在的代码块内有效，在块级作用域内有效
3. let不允许在相同作用域中重复声明，注意是相同作用域，不同作用域有重复声明不会报错

### const
1. const声明一个只读的变量，声明后，值就不能改变
2. const必须初始化
3. const并不是变量的值不能改动，而是变量指向的内存地址所保存的数据不得改动


### 区别
1. 变量提升
   + ar声明的变量存在变量提升，即变量可以在声明之前调用，值为undefined
   + let和const不存在变量提升，即它们所声明的变量一定要在声明后使用，否则报错
2. 块级作用域
   + var不存在块级作用域
   + let和const存在块级作用域
3. 重复声明
   + var允许重复声明变量
   + let和const在同一作用域不允许重复声明变量

4. 修改声明的变量
   + var和let可以
   + const声明一个只读的常量。一旦声明，常量的值就不能改变，但对于对象和数据这种引用类型，内存地址不能修改，可以修改里面的值。
