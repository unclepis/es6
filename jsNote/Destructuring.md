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
### keypoint:
- 数组解构是一种匹配模式，左右数据进行 有序的 懒匹配 
- 根据左右数据，可以分成解构不成功和不完全解构两种
- 对于默认参数只有在严格模式下，也就是匹配到undefined的时候才会生效，否则都是懒匹配

## 对象解构赋值
- 1.数组的元素需要根据顺序进行解构赋值，而对象是按照key进行解构，所以名字必须要一致

``` 
  let {name,age} = {name:'pis',age:18}
  let {age,name} = {name:'pis',age:18} // 顺序不影响对象的解构
  let {ages} = {name:'pis',age:18} 
  ages // undefined key值不匹配的话undefined
  name // pis
  age // 18
```
- 2.对象key值与属性名不一致,需要对key值进行转换

```
  let {name:user} = {name:'pis'}
  // user pis
```
因为实际上对象的解构赋值是 let{first:first,last:last} = {first:'uncle',last:'pis'} 的一种简写let{first,last} = {first:'uncle',last:'pis'} 

- 3.解构也可以用于嵌套结构的对象,但是需要注意的是它只能解析变量，不能解析模式

```
  var node = {
  loc: {
    start: {
      line: 1,
      column: 5
    }
  }
};
var { loc: { start: { line }} } = node; // loc是模式解构不了，start也是默认，只用line和column是变量可以解析
```

- 4.对象的解构也可以指定默认值

```
  let {info,user='pis'} = {info:'userName'} // 也是和数组一样 严格模式下懒加载
```
