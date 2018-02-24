# self-learning of ES6 new characters

## let and const
### let
- 1.let声明的变量只在它所在的代码块有效

```
  {
    let info = 'hello world'
  }
  console.log(info) // info is not defined
```
常见的就是for循环中对于全局变量的定义，避免全局变量被在for循环中被修改

- 2.没有了变量提升，必须要先定义在使用

```
  console.log(infoVar); // undefined
  console.log(infoLet); // info is not defined
  let infoLet = 'hello world'
  var infoVar = 'hello world'
```

- 3.暂时性死区:在代码块内，使用let命令声明变量之前，该变量都是不可用的。这在语法上，称为“暂时性死区”（temporal dead zone，简称TDZ）。

```
  // TDZ开始
  console.log(infoLet) // info is not defined
  let infoLet // TDZ结束
  console.log(infoLet) // undefined
  infoLet = 'hello world'
  console.log(infoLet) // hello world
```
- 4.不允许重复定义

```
  let infoLet = 'hello world'
  let infoLeft = 'uncle pis' // infoLet has already exist
```
