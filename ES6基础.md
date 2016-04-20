摘自 [【阮一峰】](http://es6.ruanyifeng.com/)
### let 和 const
  1 let 所声明的变量，只在let命令所在的代码块内有效。(for循环的计数器，就很合适使用let命令)
  2 let不像var那样会发生“变量提升”现象。所以，变量一定要在声明后使用，否则报错。
  3 ES6明确规定，如果区块中存在let和const命令，这个区块对这些命令声明的变量，从一开始就形成了封闭作用域。凡是在声明之前就使用这些变量，就会报错。
  4 let不允许在相同作用域内，重复声明同一个变量。
  (ES6也规定，函数本身的作用域，在其所在的块级作用域之内。)
  
  
  1 const也用来声明变量，但是声明的是常量。一旦声明，常量的值就不能改变。
  2 const一旦声明变量，就必须立即初始化，不能留到以后赋值。
  3 const的作用域与let命令相同：只在声明所在的块级作用域内有效。
  4 const命令声明的常量也是不提升，同样存在暂时性死区，只能在声明的位置后面使用。
  5 const声明的常量，也与let一样不可重复声明。

对于复合类型的变量，变量名不指向数据，而是指向数据所在的地址。const命令只是保证变量名指向的地址不变，并不保证该地址的数据不变，
所以将一个对象声明为常量必须非常小心。
    ```javascript
      const foo = {};
      foo.prop = 123;
      
      foo.prop
      // 123
      
      foo = {} // TypeError: "foo" is read-only
    ```
上面代码中，常量foo储存的是一个地址，这个地址指向一个对象。不可变的只是这个地址，即不能把foo指向另一个地址，但对象本身是可变的，
所以依然可以为其添加新属性。
  
  ES6除了添加let和const命令，另外两种声明变量的方法：import命令和class命令。所以，ES6一共有6种声明变量的方法。
  如：
  ```javascript
    // constants.js 模块
    export const A = 1;
    export const B = 3;
    export const C = 4;
    
    // test1.js 模块
    import * as constants from './constants';
    console.log(constants.A); // 1
    console.log(constants.B); // 3
    
    // test2.js 模块
    import {A, B} from './constants';
    console.log(A); // 1
    console.log(B); // 3
  ```
全局对象是最顶层的对象，在浏览器环境指的是window对象，在Node.js指的是global对象。ES5之中，全局对象的属性与全局变量是等价的
这种规定被视为JavaScript语言的一大问题，因为很容易不知不觉就创建了全局变量。ES6为了改变这一点，一方面规定，var命令和function命令声明的全局变量，依旧是全局对象的属性；另一方面规定，let命令、const命令、class命令声明的全局变量，不属于全局对象的属性。
```javascript
var a = 1;
// 如果在Node的REPL环境，可以写成global.a
// 或者采用通用方法，写成this.a
window.a // 1

let b = 1;
window.b // undefined
```
上面代码中，全局变量a由var命令声明，所以它是全局对象的属性；全局变量b由let命令声明，所以它不是全局对象的属性，返回undefined。


# 传统上，JavaScript只有indexOf方法，可以用来确定一个字符串是否包含在另一个字符串中。ES6又提供了三种新方法。

  includes()：返回布尔值，表示是否找到了参数字符串。
  startsWith()：返回布尔值，表示参数字符串是否在源字符串的头部。
  endsWith()：返回布尔值，表示参数字符串是否在源字符串的尾部。

# repeat方法返回一个新字符串，表示将原字符串重复n次。

# ES7推出了字符串补全长度的功能。如果某个字符串不够指定长度，会在头部或尾部补全。padStart用于头部补全，padEnd用于尾部补全。
  ``` javascript
    'x'.padStart(5, 'ab') // 'ababx'
    'x'.padStart(4, 'ab') // 'abax'
    
    'x'.padEnd(5, 'ab') // 'xabab'
    'x'.padEnd(4, 'ab') // 'xaba'
    
    'xxx'.padStart(2, 'ab') // 'xxx'
    'xxx'.padEnd(2, 'ab') // 'xxx'
    
    'abc'.padStart(10, '0123456789')
      // '0123456abc'
      
    'x'.padStart(4) // '   x'
    'x'.padEnd(4) // 'x   '
  ```

# 模板字符串 `
 它可以当作普通字符串使用，也可以用来定义多行字符串，或者在字符串中嵌入变量。
 变量名写在${}之中
  ```javascript
    $("#result").append(`
      There are <b>${basket.count}</b> items
       in your basket, <em>${basket.onSale}</em>
      are on sale!
    `);
 ```
# ES6提供了二进制和八进制数值的新的写法，分别用前缀0b（或0B）和0o（或0O）
### ES6在Number对象上，新提供了Number.isFinite()和Number.isNaN()两个方法，用来检查Infinite和NaN这两个特殊值。
### Number.isFinite()用来检查一个数值是否非无穷（infinity）。
### Number.isNaN()用来检查一个值是否为NaN。
### ES6将全局方法parseInt()和parseFloat()，移植到Number对象上面，行为完全保持不变。
###### Number.isInteger()用来判断一个值是否为整数。需要注意的是，在JavaScript内部，整数和浮点数是同样的储存方法，所以3和3.0被视为同一个值。
### Number.isSafeInteger()则是用来判断一个整数是否落在这个范围之内。
### Math.trunc方法用于去除一个数的小数部分，返回整数部分。
### Math.sign方法用来判断一个数到底是正数、负数、还是零。
   它会返回五种值。
    参数为正数，返回+1；
    参数为负数，返回-1；
    参数为0，返回0；
    参数为-0，返回-0;
    其他值，返回NaN。
### Math.cbrt方法用于计算一个数的立方根。
### Math.imul方法返回两个数以32位带符号整数形式相乘的结果，返回的也是一个32位的带符号整数。
### Math.fround方法返回一个数的单精度浮点数形式。
### Math.hypot方法返回所有参数的平方和的平方根。
