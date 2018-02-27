# 数组/对象/字符串/函数解构赋值
## 解构赋值常用操作
- 1.交换位置 let [x,y] = [1,2]  [x,y] = [y,x]
- 2.从函数返回多个值

```
 function test(){
    return [a,b,c]
 }
 let [a,b,c] = test()
 let{x,y} = test1() // 对象的解构一样
 
 这个在es6中import模块中的部分经常使用
 在react中经常有import React,{Component} from 'react'
 import{connect} from 'redux' 其实都是对解构的使用
```
- 3.将函数的参数对应起来

```
  function test({name,age}){
    console.log(`name is ${name} and age is #{age}`) // 将参数的name和age和函数内部的参数对应起来
  }
```
- 4.提取数据

```
  var info = {
    name:'pis',
    relatives:[
      father:'piss',
      mother:'pisss'
    ]
  }
  let {name,relatives:parents} = info // 方便的提取数据，如果需要，还可以修改参数的名字
  // name pis parents是个数组
```
- 5.函数默认参数设置

```
  $.ajax = function(
    url,
    method = 'get',
    success = function(){}
  ){
    
  }
```
- 6.Map遍历

```
  let map = new Map()
  map.set('name','pis')
  for (let {key,value} of map){
	  console.log(`${key} is ${value}`)
}
```
- 7.模块导入 

```
  import {conncet} from 'redux'
  import {Provider} from 'react-redux'
  import {createStore} from 'redux'
```


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
- 5.需要注意，如果声明和赋值分开，需要用()括起来，要不然js会当做块级作用域

```
  let info; ({info} = {info:'userName'}) // 不用括号括起来会报错
```
- 6.数组是特殊的对象，所以可以用索引对数组进行对象的解构赋值

```
  let arr = [1,2,3]
  let {0:first,[arr.length-1]:last} = arr;  // 方括号是属性名表达式
  first // 1   last // 3
```
### 字符串解构赋值
- 1.字符串能够进行解构赋值，是因为字符串是一个类数组
```
  const [a,b,c,d,e] = 'hello';
  a //h
```
- 2.因为字符串有lenth属性，所以可以对字符串的长度length进行对象的解构赋值
```
  const {length} = 'hello'
  length // 5
```
### 函数结构赋值
- 1.参数会被进行对象或者数组的解构赋值

```
  function test([a,b]){
    return a+b
  }
  // test([1,2]) 这样可以优化参数的结构
  // 函数add的参数表面上是一个数组，但在传入参数的那一刻，数组参数就被解构成变量x和y。对于函数内部的代码来说，它们能感受到的
参数就是x和y。
  [[1,2],[3,4]].map([a,b]=>a+b) // [3,7]
  
  function move({x, y} = {}) {
      return [x, y];
  }
  move({x:'pis',y:18})  // ['pis',18]
```
- 2.也可以给参数设置默认参数

```
  funcion test({x=0,y=1}={}){
    return [x,y]
  }
  test() // [0,1]
```
### keypoint：
- 对象解构赋值，只能解构变量，不能解构模式
- 对象的结构赋值因为要匹配key而和顺序无关，所以一般需要key一样，如果需要改key需要使用：进行重命名
- 对象和结构赋值和数组一样可以设置默认值{x=1}={},也是在undefined下生效
