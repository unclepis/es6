## 数组解构赋值
- 1.从数组和对象中提取值，对变量进行赋值，这被称为解构（Destructuring）。
- 2.本质上，这种写法属于“模式匹配”，只要等号两边的模式相同，左边的变量就会被赋予对应的值
  1)解构不成功
    左边的变量 在 右边有不匹配的  let [a,b] = [1]  b就是解构不成功，会返回undefined
  2)不完全解构
    左边的变量 匹配 右边部分变量 let[a]=[1,2] 
- 3.如果解构不成功，变量的值就等于undefined。
- 4.ES6内部使用严格相等运算符（===），判断一个位置是否有值。所以，如果一个数组成员不严格等于undefined，默认值是不会生效的。
  
```
  var [foo='test'] = []; // foo  'test'
  var [bar, foo='test'] = [1]; // bar 1  foo test  test就是默认值
  var [bar, foo='test'] = [1,null]; // bar 1 foo null
```
- 3.常用使用

```
  let [a, b, c] = [1, 2, 3]; // 基本使用
  let arr = [1,2,3,4,5]; let arr1 = [...arr] // 复制一份arr给一个新的数组arr1
  let [a,b,...c] = [1,2,3,4,5,] // a=1,b=2,c=[3,4,5] 
  let [a,,b] = [1,2] // a =1 b= undefined
  let [x, , y] = [1, 2, 3]; x =1 y =3 
  let [x, y, ...z] = [1]; x = 1 y = undefined z=[] 
```