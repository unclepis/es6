## js的作用域：
- 全局作用域
- 函数作用域
- eval作用域
- 新增块级作用域

### 块级别作用域
- 由于js有变量提升，所以块级作用域避免变量的覆盖

```
  var info = 'uncle'
  function func(){
    console.log(info) // 由于变量提升，undefined
    if(true){
      var info ='pis'
    }
  }
  ```
- 例如for循环计数的i会导致全局变量的污染，块级作用域只在for循环的函数体内有效
- 利用块级作用域，可以隔离变量，类似于IIFE的自执行函数的功能

```
  {
    let info='uncle'
    {
      let info = 'pis'
      console.log(info) // pis
    }
    console.log(info) // uncle
  }
```
1.ES6允许块级作用域的任意嵌套。
2.在不同的{}块级作用域中可以定义同名变量，外层作用域无法读取内层作用域的变量
