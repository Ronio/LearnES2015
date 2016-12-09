# Set 和 Map数据结构

ES6提供了新的数据结构Set。它类似于数组，但是成员的值都是唯一的，没有重复的值。

```js
var s = new Set();
[2, 3, 5, 4, 5, 2, 2].map(x => s.add(x));

for (let i of s) {
    console.log(i);
}

// 去除数组的重复成员
[...new Set(array)]
```

## Set实例的属性和方法

### 实例属性
- Set.prototype.constructor: 构造函数，默认就是Set函数
- Set.prototype.size: 返回Set实例的成员总数

### 实例方法 之 操作数据
- add(value)：添加某个值，返回Set结构本身。
- delete(value)：删除某个值，返回一个布尔值，表示删除是否成功。
- has(value)：返回一个布尔值，表示该值是否为Set的成员。
- clear()：清除所有成员，没有返回值。

```js
// 利用Set中存储唯一值的特性，去除数组重复值
function dedupe(array) {
    return Array.from(new Set(array));
}

dedupe([1, 2, 2, 3]);  // [1, 2, 3]
```

### 实例方法 之 遍历操作
- keys()：返回键名的遍历器
- values()：返回键值的遍历器
- entries()：返回键值对的遍历器
- forEach()：使用回调函数遍历每个成员

*注意：Set的遍历顺序就是插入顺序*


### WeakSet

WeakSet与Set类似，区别就是：  
1. WeakSet的成员只能是对象，而不能是其他类型的值
2. WeakSet中的对象都是弱引用，就是垃圾回收机制不考虑WeakSet对该对象的引用。

WeakSet实例不能遍历，有三个方法：  
1. WeakSet.prototype.add(value)：向WeakSet实例添加一个新成员。
2. WeakSet.prototype.delete(value)：清除WeakSet实例的指定成员。
3. WeakSet.prototype.has(value)：返回一个布尔值，表示某个值是否在WeakSet实例之中。

## Map

键值对的集合，任意类型的值都可以作为键

```js
var array = [
    ['name', {}],
    ['age', 17]
];

var m = new Map(array); // {name: {}, age: 17}
```

TODO： 各种对象之间地转换需要实操

### WeakMap
WeakMap结构与Map结构基本类似，唯一的区别是它只接受对象作为键名（null除外），不接受其他类型的值作为键名，而且键名所指向的对象，不计入垃圾回收机制。
