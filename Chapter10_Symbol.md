# Symbol 数据类型

ES5: Undefined, Null, Boolean, String, Number, Object  
ES2015: Symbol  原始数据类型

凡是属性名属于Symbol类型，就是独一无二的，保证不会与其他属性名产生冲突

``` js
let s = Symbol();

typeof s  // "symbol"
```

Symbol值可以转换为布尔值，不能转为数值

可以设置为对象得属性名

``` js 
const bar = Symbol();
var obj = {
    [bar]: function() {
        // some code
    }
}
```

## 属性名的遍历

Symbol 作为属性名，该属性不会出现在for...in、for...of循环中，也不会被Object.keys()、  
Object.getOwnPropertyNames()、JSON.stringify()返回。但是，它也不是私有属性，有一个  
Object.getOwnPropertySymbols方法，可以获取指定对象的所有 Symbol 属性名。

Object.getOwnPropertySymbols方法返回一个数组，成员是当前对象的所有用作属性名的 Symbol 值。

## Symbol.for() AND Symbol.keyFor()

``` js
var s1 = Symbol.for('hu');
var s2 = Symbol.for('hu');

// s1 === s2

Symbol.keyFor(s2);  // "hu"
```

*注意： Symbol.for为Symbol值登记的名字，是全局环境的，可以在不同的 iframe 或 service worker 中取到同一个值。*

## TODO: 内置得Symbol值
// ES6提供了11个内置得Symbol值