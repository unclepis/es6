# python syntax
## indent
- python的语法比较简单，使用缩进的方式，缩进的语句被视为代码块
- 一般的约定是四个空格的缩进
## input and print
- input() 为输入函数，可以设置输入前的提示信息input('Please input the value')
- print() 为输出函数 打印输出信息 print(123)/print('hello world')
  1.print()函数可以接受多个字符串，用逗号隔开，就可以练成一串输出,遇见逗号会输出一个空格
  
  ```
    name = input('Please input your name')
    print('user/'s name is ',name)
    print('100 + 200 = ',100+200) // 在引号里面的被当做字符串解析，后面当做表达式进行计算
  ```
## 变量
  - python也是动态语言，所以声明一个变量也没有定义其类型
  - python是大小写敏感的
  - 数据类型
  
  1）int整数
  
    - python可以处理任意大小的整数，没有数据区间
    - python中对整型，有两种除法运算：一种是/，计算的结果不管是否整除都是浮点数
    ```
      10/3 //3.3333333333333333333
      9/3 //3.0
    ```
    还有一种叫地板除//，只保留整数除法的整数位
    ```
      1//3   // 0
      10//3  // 3  
    ```
    而对整数也有求余数的运算10%3 //1 所以说对整数的运算都是精确的，结果永远都是整数(除法可以使用地板除啊)
   2）float浮点数
  
    - 对于很大或者很小的浮点数，就必须用科学计数法表示，它也没大小区间限制，但是超过一定范围就会提示inf无穷
    - 整数和浮点数在计算机内部存储的方式是不同的，整数运算永远是精确的，也包括除法；而浮点数会存在四舍五入误差
  3）string字符串
  
    - 可以是单引号或者是双引号，但是不能混用
    - 引号不只是字符串的一部分
    - 在单引号和双引号混合使用的时候，可以使用转义字符\来标识 "i\'m uncle pis" // i'm uncle pis
    - r' '的引号中间的特殊字符不会进行转义，print(r'i \'m uncle pis') // i\'m uncle pis
    - r''' ''' 可以进行标识多行内容
   
    ```
      print(r'''
        line1
        line2''') 
    ```
  4）boolean布尔值
  
    - True/False // 注意是首字母大写，python是严格的区分大小写的
    - 布尔值可以使用and,or,not运算表示与运算，或运算和非运算
  5）空值
  
    - None // 注意不是js中的null，None也不是0，是一种特殊的空值
    
  6）其他
  
    - list [1,2,3] 有序集合
    ```
      userName=['pis','eric']
      len(username) // 2
      userName[0] // pis
      userName[-1] // 取最后一个元素的快捷表示，一次类推userName[-2]
    ```
      - 去长度使用len()方法
      - 取元素使用index索引，也可以使用负值从后往前取元素
      - 也可以使用append()方法追加元素，相当于js数组的push方法
      - 也可以使用insert(index,item)在指定的位置插入元素 // userName.insert(1,'cindy')  ['pis','eric','cindy']
      - 也可以使用pop()删掉元素 // userName.pop() 和js数组的pop方法一样，删掉末尾的元素
      - pop(index)是删掉index上的元素
      - 修改元素使用赋值语句 // userName[1] = 'xindy'
      - list里面数据结构可以不一样 //data = ['people',111,True,['test']]
      - 如果list里面的元素是list，就相当于一个多维数组 data[3][0]  test
      - name = []  len(name)就等于0，也就是一个空的list
    - tuple元组 (1,2,3)
      - 有序列表
      - 和list很相似，但是tuple一旦初始化就不能修改
      - classMate = ('pis','eric') 因为不能修改，所以没有append和insert，pop等方法
      - 但是读取数据是可以的，classMate[-1]  eric,但是不能赋值成别的元素
      - 如果要定义有一个元素的tuple，需要写一个，否则会被当做括号解析 name= ('pis',)
      - 注意tuple中如果有list，list的值是可以修改的，但是tuple还是指向该list，所以tuple还是没有被修改，和es6定义的引用类型const一样
     - dist {key:value}
    - set new set([1,2,3]) // 接的参数是list，因为set是key不能重复，所以set中不能有重复项
    - 自定义类型
## 数据类型校验
  - isinstance(variable,type) 
  
  ```
    name = '123' 
    isinstance(name,string)
    isinstance(name,(string,int)) // name为string或者int类型的实例 会返货boolean  
  ```
## 条件判断
  - python的条件判断和js的一样，只是syntax用缩进和冒号
  ```
    name = 10
    if name>1: // 别忘记写：，而且if的条件不用使用括号括起来
      print('user is more than 1') // python里面缩进代表代码块
    elif name>18: // elif是else if的缩写
      print('user is more than 18')
    else:
      print('user is a adult')
  ```
  - if elif else和js的条件判断一样，每个场景是互斥的，也就是说从上往下执行，当满足条件了其他分支是不会运行的
## 循环
  - python提供两种循环 
  
  for...in依次把list或tuple中的元素迭代出来
  
  ```
    for age in list(range(5)):
      print(age); // 0,1,2,3,4
  ```
  while循环
  
  ```
    n = 10
    sum=0
    while n>0:
      sum = sum+n;
      n=n-1;
    print(sum) // 1-10求和
  ```
## 常量
  - 所谓常量就是不能变的变量
  - 通常用全部大写的变量名表示一个常量。例如PI
  - python没有任何机制阻止常量被修改，但是这都是默认的习惯
## 备注
  - 以#开头的语句是备注
## 工具函数
- len()
- isinstance()
- append()
- insert()
- pop()
- int()
- list()
- range()
  

