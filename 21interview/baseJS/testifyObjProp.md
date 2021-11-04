## 查询某个对象是否有某个属性的方法
### 使用in关键字
该方法可以判断对象的自有属性和继承来的属性是否存在。

### 使用对象的hasOwnProperty()方法
该方法只能判断自有属性是否存在，对于继承属性会返回false。

### 使用undefined判断
自有属性和继承属性均可判断。
```js
var o={x:1};
o.x!==undefined;    //true
o.y!==undefined;    //false
o.toString!==undefined  //true

```

> 该方法存在一个问题，如果属性的值就是undefined的话，该方法不能返回想要的结果，如下:

```js
var o={x:undefined};
o.x!==undefined;    //false，属性存在，但值是undefined
o.y!==undefined;    //false
o.toString!==undefined  //true
```

### 在条件语句中判断
```js
var o={};
if(o.x) o.x+=1; //如果x是undefine,null,false," ",0或NaN,它将保持不变
```

### propertyIsEnumerable() 
propertyIsEnumerable() 是hasOwnProperty() 的增强版，这个方法的用法与hasOwnProperty()相同，但当检测属性是自有属性(非继承)且这个属性是可枚举的，才会返回true。