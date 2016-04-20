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
