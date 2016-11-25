# javascript-Concept
Some reference for syntax and concept of javascript

##Object.assign()
Source: [JavaScript | MDN](https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Global_Objects/Object/assign)

The Object.assign() method is used to copy the values of all enumerable own properties from one or more source 
objects to a target object. It will return the target object.

###Syntax
> Object.assign(target, ...sources)

###Parameters
target
> The target object.

sources
> The source object(s).

###Return value
> The target object.

##Example
###Cloning an object
```javascript
var obj = { a: 1 };
var copy = Object.assign({}, obj);
console.log(copy); // { a: 1 }
```

###Merging objects
```javascript
var o1 = { a: 1 };
var o2 = { b: 2 };
var o3 = { c: 3 };

var obj = Object.assign(o1, o2, o3);
console.log(obj); // { a: 1, b: 2, c: 3 }
console.log(o1);  // { a: 1, b: 2, c: 3 }, target object itself is changed.
```

###Merging objects with same properties
```javascript
var o1 = { a: 1, b: 1, c: 1 };
var o2 = { b: 2, c: 2 };
var o3 = { c: 3 };

var obj = Object.assign({}, o1, o2, o3);
console.log(obj); // { a: 1, b: 2, c: 3 }
```