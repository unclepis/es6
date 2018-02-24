## const
- 1.只读属性，一旦定义不能改变

```
  const variable = 1949;
  variable  = 2018 // Assignment to constant variable
```
- 2.声明和初始化必须同时进行

```
  const variable // Missing initializer in const declaration
```
- 3.作用域与let命令相同：只在声明所在的块级作用域内有效
- 4.命令声明的常量也是不提升，同样存在暂时性死区，只能在声明的位置后面使用。
- 5.声明的常量，也与let一样不可重复声明
- 6.const命令只是保证变量名指向的地址不变，并不保证该地址的数据不变

```
  const test2 = {name:'pis',age:11}
  test2={} //Assignment to constant variable. 不能修改const
  test2.nation = 'cn' // {name: "pis", age: 11, nation: "cn"}
```
