---
title: JavaScript-基础
date: 2020-10-18 23:53:19
tags: JavaScript
categories: "javascript"
top: 5
top_img:
cover: https://gitee.com/wang_hong_bin/pic-go-photos/raw/master/JavaScript.jpg
---

### 基础:

```javascript
var

let

const


window.onload = function(){
    console.log(x); // undefind
    var x = 100;
    
    console.log(x); // 直接报错
    let x = 100;
    
}
```

### `let 、const`的区别:

```javascript
1. let  和 const 不存在变量提升
```

```javascript
2. let 和 const 在同一个作用域下不能重复定义相同的一个变量名称
```

```javascript
3. let 和 const 有严格的作用域 块级作用域
```



```javascript
        window.onload = function () {
            var c = 10;
            var c = 99;
            console.log(c); // 99

            let d = 10;
            let d = 20;
            console.log(d); // Uncaught SyntaxError: Identifier 'd' has already been declared
        }

```

+ `const`

  ```javascript
          const a = 10;
          a = 20;
          console.log(a); // TypeError: Assignment to constant variable.
  ```

+ `let`

  ```javascript
      let age = 12;
      age = 30;
      console.log(age); // 30
  ```



```javascript
作用域:
    1. 全局作用域 
    2. 局部作用域
    
    var 属于函数作用域 -- > 全局

    // var 关键字
    function f(){
        var a = 100;
        if(true){
            var a = 1000;
        }
    	console.log(a);
	}
	f(); // 输出结果: 1000 

```

```javascript
	let -- > 块级作用域

    // let、const 关键字
    function f() {
       let a = 100;
       if (true) {
         let a = 1000;
      }
       console.log(a);
    }
    f(); // 输出结果: 100
```

```javascript
const  声明一个只读的常量、一旦定义、常量的值不能改变的
```



### 箭头函数:

```javascript
1. let f = v=>v;

等价于:

var f = function(v){
    return v;
}

```

```javascript
2. var f = function(){
    return 123;
}
等价于:
	let f = ()=>123;

```

```javascript
3. let f = (n1,n2)=>n1+n2;
等价于:
	var f = function(n1,n2){
        return n1+n2;
    }
    f(10,20); // 结果: 30
```

```javascript
4. // 返回对象的箭头函数
let f = (n1, n2) => ({ n1: 10, n2: 20 });
console.log(f()); // { n1: 10, n2: 20 }

等价于:
var a = function () {
  return {
    n1: 10,
    n2: 20,
  };
};
console.log(a()); // { n1: 10, n2: 20 }


this 指向定义
```



### `Set `和 `Map`：

```javascript
// set 似与数组 成员是唯一的
var s = new Set(); 
s.add(1).add(2).add(3); // 链式添加
console.log(s); // Set { 1, 2, 3 }

// 可以添加并实现数组去重
var arr = [1, 23, 22, 23, 2];
var s2 = new Set(arr);
console.log(s2); // Set { 1, 23, 22, 2 }

```

```javascript
// ...  扩展运算 参数序列
var arr = [1,2,3];
var new_arr = [...arr];

console.log(new_arr); // 【1，2，3】


// 数组去重 并返回数组
var arrs = [1,1,4,3,5,6,6,6];
var a = [...new Set(arrs)];

console.log(a); // [ 1, 4, 3, 5, 6 ]

```

```javascript
// map 类似于对象 键值对的方式

let m = new Map();
m.set('name','gg').set('age',18);

// 快速添加 二维数组一样【[],[]】
let m2 = new Map([["name", "ggd"], ["age", 16]]); // Map的键可以是任意类型

// for of
for (let [k, v] of m2) {
  console.log((k+":"+v));
}

// 遍历的结果 
name:ggd
age:16
```



### ` JavaScript`的基本数据类型:

```javascript

1. 数字
2. 字符串
3. 布尔值
4. undefined
5. null

```

###  `&&(求 假)`:

```javascript
一假则假

var _num = 5 && 8;
console.log(_num); // 8 先判断 && 之前是否为真,为真将 && 后面的值赋给逻辑表达式

var _num = 0 && 8;
console.log(_num); // 0 前面的值为假,就将前面的值赋给逻辑表达式

```

###  `||(求 真)`:

```javascript
一真则真

var _num = 5 || 8;
console.log(_num); // true  先判断 || 之前是否为真,如果为真将值赋逻辑表达

var _num = 0 || 8;
console.log(_num); // true // 如果前面得值为假,那么就取后面得值赋给逻辑表达式

```

###  `！` :

```javascript
非真即假,非假即真
```

##  `&&、||、！`:

```javascript

var a = 10;
console.log(a > 8 && a < 9); //  false 先判断 && 之前是否为真,为真将 && 后面的值赋给逻辑表达
console.log(a > 8 && a < 100); // true 
console.log(a < 0 || a > 8); //  true
console.log(a > 100 || a < 0); // false
console.log(a > 10 / 2 && a < 10 % 8); // false
console.log(!(a > 0)); // false
console.log(!(a > 10 / 2 + 3) || a < (10 % 8) * 6); //  true



**
    a = 0 && 8;
	console.log(a); // 0
	var b = a > 8 && a < 9; //false

```

###   三目运算符:

```javascript
三目运算符: 

    先执行第一个表达式(也就是 ? 前面的表达式),看这个表达式是否为真
    如果第一个表达式的值为真,那么吧冒号前面的值,赋值给整个表达式
    如果第一个表达式的值为假,那么吧冒号后面的值,赋值给整个表达式
          
var year = 2020;
var _year = ( year % 4 ==0 && year % 100 != 0 || year % 400 == 0) ? console.log('润年') : console.log('平年');
console.log(_year); // 闰年

var a = 6;
var b = 7;
var c = a > 0 ? ++b + a++ : --a + b; 
// console.log(++b,a++,--a+b); 8 6 14
console.log(c); //  14

```

###  比较运算符：

> + `==` 判断的是`值`是否一致
> + `===`判断的是`类型`和`值`是否都一致 都一致才会为 `true`  严格判断

###  数据类型的转换:

1. 数据类型的强制转换

   + `number()` 强制将一个其他类型的数据转换为数字类型,转不了就是 `NaN`

     ```javascript
     
     var _Isnum;
     _Isnum = '1';
     console.log(Number(_Isnum)); // 1
     
     _Isnum = '  '; 
     console.log(Number(_Isnum));// 0
     
     _Isnum = 'aa123asas' 
     console.log(Number(_Isnum)); // NaN
     
     _Isnum = 1.3
     console.log(Number(_Isnum)); // 1.3 
     
     ```

     + 通常情况下是用来转字符串的
       + 如果字符串整体是一个数字,那么就转化为这个`数子`
       + 如果字符串是一个`特殊的空字符串`,那么就转换为`0`,
       + 如果字符串整体来看不是一个数字,那就转换为`NaN`

   + `String()` 强制将一个其他类型数据转换为字符串类型

     ```javascript
     var IsString = 1;
     IsString = String(IsString);
     console.log(typeof IsString); // string
     ```

   + `Boolean()` 强制将一个其他类型数据转化为 `boolean`类型

     ```javascript
     var IsBoolean = 6;
     IsBoolean = Boolean(IsBoolean)
     console.log(IsBoolean); // true
     ```

     + 转换数字的时候,除了`0`是`false`,其余都是`true`

     + 转换字符串的时候,除了空字符串是`false`,其余都是`true`

     + 转换 `undefined`和`null`都是`false`

       ```javascript
       console.log("----------------------Boolean 转换 undefined 和 null----------------------");
       // Boolean 转换 undefined 和 null
       IsBoolean = Boolean(undefined);
       console.log(IsBoolean); //false
       
       IsBoolean = Boolean(null);
       console.log(IsBoolean); // false
       ```

2. 数据类型的隐式转换

   + 各种类型在适当的场合会发生隐式转换

     ```javascript
     
     console.log("------------------- 隐式类型的转换 -------------------");
       var a = 5;
       var b = a + 10;
       console.log(typeof b); // number b = 15
     
       var d = a + true;
       console.log(typeof d); // number d = 5
     
       var c = a + '12';
       console.log(typeof c); // string c = 512
     
     ```

   + 主要是运算和条件判断过程中

3. 数据类型的手动转换(在字符串中提取数字)

   + `parseInt()`
   + `parseFloat()`

###   语句结构分类:

#### `if`判断:

####  单分支:

```javascript

if(一般都是一个表达式,但是最终都会转化为 boolean){
  代码块; // 表达式为 true 则执行该代码块
}

```



>   双分支(三元表达式)

##### `if`判断案例

+ 单分支(输入钱数,如果超过 `100`万我就去学习)

  ```javascript
  var money = 10000000;
  if (money > 1000000) {
    console.log("我爱学习!");
  }
  ```

+ 双分支
  + 天气好就去看电影,不好就写代码
  
  ```javascript
    var weather = "sunday";
    if (weather == sunday) {
      console.log("天气很好,今天我该出去看电影了!");
    } else {
      console.log("算了,今天又是应该努力的时候了!");
    }
  ```
  
  + 输入一个数,这个数大于`0`就继续写代码,不大于`0`，嗯嗯，我应该睡觉了!
  
    ```javascript
    var _number = parseInt(prompt("请输入一个数字: "));
    if (_number > 0) {
      console.log("继续写代码··········");
    } else {
      console.log("enen,我应该睡觉了········");
    }
    ```
  
+ 多分支
  + 输入体重判断属于什么样的体重
  
  ```javascript
    var _weight = parseFloat(prompt("请输入你的体重: "));
    if (_weight < 50) {
      console.log("你需要稍微补充一些能量················");
    } else if (_weight < 60) {
      console.log("请保持·············");
    } else if (_weight < 70) {
      console.log("请您每天坚持锻炼···········");
    } else {
      console.log("接下来,让我们··········");
    }
  ```
  
  + 输入钱数,根据钱的数量去购买新设备
  
    ```javascript
    var _moneyE = parseFloat(prompt("请输入你拥有的钱数: "));
    if (_moneyE < 30) {
      console.log("买鼠标·········");
    } else if (_moneyE >= 100 && _moneyE <= 300) {
      console.log("买键盘···········");
    } else if (_moneyE >= 2000 && _moneyE <= 5000) {
      console.log("我可以买全新的设备了············");
    } else {
      console.log("算了,我可以在等等·············");
    }
    ```
  
+ 分支嵌套
  + `92`汽油和`96`号汽油
  + 92号汽油单价`5元/L` 如果加的超过`30L`就`4元/L`
  + `96`号汽油单价`6元/L` 如果加超过`40L`就`5元/L`
  + 最后花了多钱?

###  `switchcase`分支语句:

+ 输入一个数字,判断是星期几

  ```javascript
  
  var _date = parseInt(prompt("请输入1~7之间的数: "));
  switch (_date) {
    case 1:
      console.log("星期一");
      break;
    case 2:
      console.log("星期二");
      break;
    case 3:
      console.log("星期三");
      break;
    case 4:
      console.log("星期四");
      break;
    case 5:
      console.log("星期五");
      break;
    case 6:
      console.log("星期六");
      break;
    case 7:
      console.log("星期日");
      break;
    default:
      console.log("请输入有效数字··········");
      break;
  }
  ```

+ 输入分数,判断优良差和不及格

  ```javascript
  
  var _score = parseInt(prompt("请输入分数: "));
  switch (_score>0) {
    case _score > 0 && _score < 60:
      console.log("不及格···");
      break;
    case _score >= 60 && _score <= 75:
      console.log("中等···");
      break;
    case _score >= 75 && _score <= 85:
      console.log("良好···");
      break;
    case _score >= 85 && _score <= 100:
      console.log("优秀···");
      break;
    default:
      console.log("请输入有效成绩···");
      break;
  }
  ```

  

###  `for`循环:

+ 循环的含义(为什么要循环)

+ 循环语法

  + 打印 `1~100`之间的数
  
    ```javascript
  for (var i = 1; i <= 100; i++) {
      console.log(i);
    }
    ```
  
  + 打印`1~100`之间的偶数
  
    ```javascript
    for (var i = 1; i <= 100; i++) {
      if (i % 2 == 0) {
        console.log(i);
      }
    }
    ```
  
  + 计算`1~100`的数字和
  
    ```javascript
    var _sum = 0;
    for (var i = 1; i <= 100; i++) {
      _sum += i;
    }
    console.log(_sum);
    ```

###   强化练习:

+ 打印`100~300`之间所有能被`3`或者`7`整除的数

  ```javascript
  for (var i = 100; i <= 300; i++) {
    if (i % 3 == 0 || i % 7 == 0) {
      console.log(i);
    }
  }
  ```

+ 打印三位数位上有`3`或者`7`的数字

  ```javascript
  for (var i = 100; i < 999; i++) {
    var _g = (i % 10) % 10;
    var _s = parseInt((i / 10) % 10);
    var _b = parseInt(i / 100);
    var _res =  _g == 3 || _g == 7 || _s == 3 || _s == 7 || _b == 3 || _b == 7;
    if (_res) {
      console.log(i);
    }
  }
  ```

+ 计算`100`的阶乘 == `1*2*3···*100`

  ```javascript
  var _Multiply = 1;
  for (var i = 1; i <= 100; i++) {
    _Multiply *= i;
  }
  console.log(_Multiply);
  ```

+ 求 `100-999`之间的水仙花数`Eg. abc = a^3+b^3+c^3`

  ```javascript
  for (var i = 100; i <= 999; i++) {
    var _g = (i % 10) % 10;
    var _s = parseInt((i / 10) % 10);
    var _b = parseInt(i / 100);
    var _res = _g * _g * _g + _s * _s * _s + _b * _b * _b;
    if (i == _res) {
      console.log(i);
    }
  }
  ```

+ 输出`100-200`之间所有的素数(质数)(只能被`1`和自身整除的数)

  + 方法一`标志位`

    ```javascript
    var flag = true;
    for (var i = 100; i <= 200; i++) {
      for (var j = 2; j < i; j++) {
        if (i % j == 0) {
          flag = false;
          break;
        }
      }
      // falg = false
      if (flag) {
        // 不会执行
        console.log(i);
      }
      flag = true; // 重置标志位 因为每个数都要重新去循环执行
    }
    ```

  + 计数

    ```javascript
    var num = 0;
    for (var i = 100; i <= 200; i++) {
      for (var j = 1; j <= i; j++) {
        if (i % j == 0) {
          num++;
        }
      }
        // num == 2 暂时没理解
      if (num == 2) {
        console.log(i);
      }
      num = 0;
    }
    ```

    

+ 求`1!+2!+3!+···+20!`的值

  ```javascript
  var _Multiply = 1;
  var sum = 0;
  for (var i = 1; i <= 20; i++) {
    // 内层循环进行累乘
    for (var j = 1; j <= i; j++) {
      _Multiply *= j;
    }
    sum += _Multiply;
    _Multiply = 1;
  }
  console.log(sum);
  ```

+ 完成一个等腰直角三角形的打印

  ```javascript
  for (var i = 0; i < 7; i++) {
    // j 打印空格
    for (var j = 0; j < 6 - i; j++) {
      document.write("&nbsp;");
    }
    // k 打印星
    for (var k = 0; k < 2 * i + 1; k++) {
      document.write("*");
    }
    document.write("<br>");
  }
  
  效果图:
        *
       ***
      *****
     *******
    *********
   ***********
  *************
  ```

  

+ 打印圣诞树

  ```javascript
  function ChristmasTree() {
    for (var i = 0; i < 7; i++) {
      // j 打印空格
      for (var j = 0; j < 6 - i; j++) {
        document.write("&nbsp;");
      }
      // k 打印星
      for (var k = 0; k < 2 * i + 1; k++) {
        document.write("*");
      }
      document.write("<br>");
    }
  }
  ChristmasTree();
  // 第二层三角形
  ChristmasTree();
  // 矩形块
  // 外层都是控制行数
  for (var i = 0; i < 3; i++) {
    // 内层完成实际操作
    for (var j = 0; j < 4; j++) {
      document.write("&nbsp;");
    }
    for (var j = 0; j < 5; j++) {
      document.write("*");
    }
    document.write('<br>');
  }
  效果图:
        *
       ***
      *****
     *******
    *********
   ***********
  *************
        *
       ***
      *****
     *******
    *********
   ***********
  *************
      *****
      *****
      *****
  ```

  

+ 打印直角三角形

  ```javascript
  for (var i = 0; i < 7; i++) {
    // k 打印星
    for (var k = 0; k < 2 * i + 1; k++) {
      document.write("*");
    }
    document.write("<br>");
  }
  
  效果:
  *
  ***
  *****
  *******
  *********
  ***********
  *************
  ```

+ 打印九九乘法口诀表

  ```javascript
  
  ```

###   `continue`与`break`关键字:

```javascript
continue; 结束当前循环 continue以下的代码块不会执行,从下一次开始继续

break; 在循环当中,跳出离他最近的那层循环,如果是多层循环要注意
```

###  对象:

```javascript
// 对象 字面量创建 姓名 年龄 性别 爱好(动作)
var Info = {
  name: "张三",
  age: 18,
  gender: "male",
  hobby: function () {
    console.log("我爱JavaScript····");
  },
};

console.log(Info);

输出:
	Info.hobby();
```

###  内置对象：

```javascript
var arr = [8, 4, 5, 6, 9, 10];

// 内置对象
if (Array.isArray(arr)) {
  console.log(arr.length);
} else {
  console.log("····");
}

```



###  数组案例:

+ 数组概念

  ```javascript
  数组概念:  数组是一个具有相同类型或者不同类型的数据有序集合
     
  为什么要有数组:
  	
  	当我们想要一次性拿到很多数据,如果没有数组,就得定义很多变量取存储
      
  ```

+ 数组`length`,索引(下标)

  ```javascript
  只要定义一个数组,数组里面就会有一个默认的属性叫 length,他代表数组的长度
  
  索引也被叫做下标,通常情况下只要我们知道了索引,就可以拿到这个数组对应的这个索引的值
  ```

+ 数组的增删改查(底层过程)

  + 数组的定义方式

    ```javascript
    var arr = [值1,值2,···];
    ```

  + 构造函数定义数组

    ```javascript
    var arr = new Array(值);
    ```

  + 在数组的末尾添加一个数

    ```javascript
    var arr = [8, 4, 5, 6, 9, 10];
    // 在数组的末尾添加一个数
    arr[arr.length] = 12;
    console.log(arr);
    
    输出:
    [
      8,  4,  5, 6,
      9, 10, 12
    ]
    ```

  + 在数组的中间添加一个数

    ```javascript
    or (var i = arr.length - 1; i >= 2; i--) {
        arr[i + 1] = arr[i];
    }
    arr[3] = 120;
    console.log(arr);
    
    输出:
        [
          8, 4,  5, 120,
          6, 9, 10
        ]
    ```

  + 在数组的头部添加一个数

    ```javascript
    for (var i = arr.length - 1; i > 0; i--) {
        arr[i + 1] = arr[i];
    }
    arr[0] = 100;
    console.log(arr)
    
    输出:
        [
          100, 4,  4, 5,
            6, 9, 10, 4
        ]
    
    ```

    + 演示

      ![Array添加底层过程](https://gitee.com/wang_hong_bin/pic-go-photos/raw/master/Array.gif)

    + 分析

      ```javascript
      var arr = [8, 4, 5, 6, 9, 10]; // arr.length = 6
      
      var i = arr.length -1; // i = 5
      arr[i+1] == arr[6]
      arr[i] = arr[5]
      
      arr[i+1] = arr[i] //  再进行理解
      
      在循环中,将元素后移···
      
      arr[0] = 100; // 就将处于首位
      ```

+ 数组删除

  + 在头部删除

    ```javascript
    var arr = [8, 4, 5, 6, 9, 10];
    
    for (var i = 1; i < arr.length; i++) {
        arr[i - 1] = arr[i];
    }
    arr.length--;
    console.log(arr);
    
    输出: [ 4, 5, 6, 9, 10 ]
    ```

  + 在中间删除

    ```javascript
    var arr = [8, 4, 5, 6, 9, 10];
    // 在中间删除
    for (var i = 4; i < arr.length; i++) {
        arr[i - 1] = arr[i];
    }
    arr.length--;
    console.log(arr);
    
    输出: [ 8, 4, 5, 9, 10 ]
    ```

  + 任意位置删除

    ```javascript
    var _index = parseInt(prompt('请输入要删除的位置: '));
    var arr = [8, 4, 5, 6, 9, 10];
    // 在中间删除
    for (var i = _index; i < arr.length; i++) {
        arr[i - 1] = arr[i];
    }
    arr.length--;
    console.log(arr);
    ```

  + 在末尾删除

    ```javascript
    var arr = [8, 4, 5, 6, 9, 10];
    arr.length--;
    console.log(arr);
    
    输出: [ 8, 4, 5, 6, 9 ]
    ```

  + 查询数组下标

    ```javascript
    // 数组查询下标*/
    for (var i = 0; i < arr.length; i++) {
        if (arr[i] == 10) {
            console.log(i)
        }
    }
    输出:
    	5
    ```

+ 数组求和

  ```javascript
  // 数组求和
  var arrys = [1, 2, 3, 4, 5];
  var sum = 0;
  for (var i = 0; i < arrys.length; i++) {
    sum += arrys[i];
  }
  console.log(sum);
  
  ```

+ 求数组最大值、最小值，平均值

  + 最大值

    ```javascript
    var arr = [8, 4, 50, 6, 9, 10];
    var max = arr[0];
    for (var i = 0; i < arr.length; i++) {
        if (arr[i] > max) {
            max = arr[i];
        }
    }
    console.log(max);
    ```

  + 最小值

    ```javascript
    var arr = [8, 4, 50, 6, 9, 10];
    var min = arr[0];
    for (var i = 0; i < arr.length; i++) {
        if (arr[i] < min) {
            min = arr[i];
        }
    }
    console.log(min);
    ```

+ 根据班级人数输入每个人的分数,求平均值

  ```javascript
  // 根据班级人数输入没个人的分数,求平均值
  var arr = [];
  var sum = 0;
  for (var i = 0; i <= 5; i++) {
    arr[i] = parseInt(prompt("请输入第" + (i + 1) + "位的分数"));
    sum += arr[i];
  }
  var average = sum / 5;
  console.log(arr);
  console.log(average);
  
  ```

+ 反转数组

  + 反转新数组

    ```javascript
    // 反转新数组
    var arr = [8, 4, 50, 6, 9, 10];
    var newArr = [];
    for (var i = arr.length - 1; i >= 0; i--) {
        newArr[newArr.length] = arr[i];
    }
    console.log(newArr);
    输出:
    	[ 10, 9, 6, 50, 4, 8 ]
    ```

  + 反转原数组

    ```javascript
    // 翻转原数组
    var arr = [8, 4, 50, 6, 9, 10];
    for (var i = 0; i < arr.length / 2; i++) {
        var temp = arr[i];
        arr[i] = arr[arr.length - 1 - i];
        arr[arr.length - 1 - i] = temp;
    }
    console.log(arr)
    
    输出:
    	[ 10, 9, 6, 50, 4, 8 ]
    ```

  + `JS方法`

    ```javascript
    
    var arr = [8, 4, 5, 6, 9, 10];
    
    arr.reverse();
    
    ```

    

+ 冒泡排序

  ```javascript
  // 冒泡排序
  var arr = [8, 4, 50, 6, 9, 10];
  // 外层循环控制轮数
  for (var i = 0; i < arr.length - 1; i++) {
      // 能层循环控制比较次数
      for (var j = 0; j < arr.length - 1 - i; j++) {
          if(arr[j]<arr[j+1]){
              var temp = arr[j];
              arr[j] = arr[j+1];
              arr[j+1] = temp;
          }
      }
  }
  console.log(arr)
  ```

+ `sort()`

  ```javascript
  var arr = [8, 4, 5, 6, 9, 10];
  arr.sort()
  
  ```

  + `sort`升序

    ```javascript
    var arr = [8, 4, 20, 5, 0, 6, 1, 9, 10];
    function compare(a, b) {
      // a 位于 b之前
      if (a < b) {
        return -1;
      } else if (a > b) {
        return 1;
      } else {
        return 0;
      }
    }
    arr.sort(compare); //升序
    console.log(arr);
    
    简化(if···else): 
    
    	return a-b
    
    ```

  + `sort`降序

    ```javascript
    // 降序
    function compare(a, b) {
      // a 位于 b之前
      if (a < b) {
        return 1;
      } else if (a > b) {
        return -1;
      } else {
        return 0;
      }
    }
    arr.sort(compare); //降序
    console.log(arr);
    
    
    简化；
    	
    	return b-a
    ```

  + `三元运算`:

+ 数组去重

  + 去除所有重复元素

    ```javascript
    var arr = [8, 4, 50, 6, 1, 2, 3, 2, 3, 4, 9, 9, 10];
    var distinct = [...new Set(arr)]
    console.log(distinct);
    输出:
        [
          8, 4, 50,  6, 1,
          2, 3,  9, 10
        ]
    ```

  + 去除数组中指定的元素

    ```javascript
    // 数组去重 指定元素去重
    var newArr = [];
    var arr = [1, 2, 3, 4, 3, 6, 3, 7, 8];
    for (var i = 0; i < arr.length; i++) {
        if (arr[i] != 3) {
            newArr[newArr.length] = arr[i];
        }
    }
    console.log(newArr);
    
    输出:
    	
    	[ 1, 2, 4, 6, 7, 8 ]
    ```

+ 合并数组,原生实现

  ```javascript
  concat(多值(逗号分隔)···)
  ```

  

+ 数组转换为字符串

  ```javascript
  
  var stringA = arr.toString();
  console.log(stringA); // 6
  console.log(typeof stringA); // string
  
  ```

  + `toString()`
  + `toLocaleString()`
  + `join()` 以指定字符分割



###  栈`(lifo last -in-first-out)`方法队列方法：

```javascript
+ push() 在数组最后一项添加

+ pop() 在数组末尾删除

+ shift() // 首个删除

+ unshift() // 首个添加
```

+ `push()`

  ```javascript
  var arr = [8, 4, 5, 6, 9, 10];
  arr.push("a", 1); // 添加两个元素
  console.log(arr);
  
  输出:
      [
        8, 4,  5,   6,
        9, 10, 'a', 1
      ]
  ```

+ `pop()`

  ```javascript
  var arr = [8, 4, 5, 6, 9, 10];
  var lastItem = arr.pop();
  console.log(lastItem);
  console.log(arr);
  输出:
  	10 // lastItem
  	[ 8, 4, 5, 6, 9 ] // 删除后的新数组
  ```

+ `shift()`

+ `unshift()`

  ```javascript
  var arr = [8, 4, 5, 6, 9, 10];
  // 首位添加元素 100
  newLength = arr.unshift(100);
  // 输出新数组长度
  console.log(newLength);
  console.log(arr);
  // 获取数组的首位元素
  var firstItem = arr.shift();
  // 100
  console.log(firstItem); 
  console.log(arr);
  
  输出:
  数组新长度: 7
  新数组:
      [
        100, 8,  4, 5,
          6, 9, 10
      ]
  首位: 100
  删除后: [ 8, 4, 5, 6, 9, 10 ]
  ```

  

+ 函数

  ```javascript
  // 函数 提示用户输入账号和密码,实现登录成功效果,再次提示
  var userId = prompt('请输入您的账号: ');
  var userpassword = prompt('请输入您的密码: ');
  
  function login(userId, userpassword) {
      if (userId == '123' && userpassword == '123') {
          alert('恭喜您,登录成功!')
      } else {
          alert('请您重新输入!')
      }
  }
  
  login(userId, userpassword);
  ```

+ 获取数组元素的索引位置

  ```javascript
  var arr = ['red','blue','add','index'];
  
   console.log(arr.indexOf('index')); // 3 只返回满足条件的第一个 没有返回 -1
  ```

+ 字符串操作(截取)

  ```javascript
  
  ```

  

###   作用域:

1. 作用域概念，作用
   + 作用域说的是变量起作用的区域或者范围
   + 作用域的作用,变量在各自的作用域当中起作用
2.  局部变量和全局变量
   + 局部变量,在局部作用域当中的变量(函数当中定义的变量)
   + 全局变量,在全局作用域当中的变量(函数外部定义的变量)



###  匿名函数:

> 
>
> 匿名函数自调用,不会发生预解析，匿名函数自调用只能执行一次,通常用来做一些项目的初始化
>
> 匿名函数自调用通常可以做:
>
> + `封装代码实现,不把代码暴露出去`
>
> + `可以防止外部的命名空间被污染`

```javascript
匿名函数语法:

    (function() {
        console.log(123)
    })();

```

###  函数的返回值:

```javascript
return 

	+ 终止函数
	+ 如果函数有 return 则返回的是 return 后面的值,如果函数没有 return 则返回 undefined
```

###  `Arguments`使用:

> 
>
> 当我们不确定有多少个参数传递的时候,可以用 `arguments` 来获取,在 `JavaScript` 中,`arguments`实际上它是当前函数的一个`内置对象`,所
>
> 有函数都内置了一个` arguments`对象,`arguments`对象中存储了传递的所有实参
>
> 

###   构造函数:

```javascript

```

