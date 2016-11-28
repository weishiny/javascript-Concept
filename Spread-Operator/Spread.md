# javascript-Concept
Some reference for syntax and concept of javascript

##Spread Operator
Source: [JavaScript | MDN](https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Operators/Spread_operator)

The spread syntax allows an expression to be expanded in places where multiple arguments (for function calls) 
or multiple elements (for array literals) or multiple variables  (for destructuring assignment) are expected.

##Example
###A more powerful array literal

Without ES2015 spread, if you have an array and want to create a new array with the existing one being part of it, 
the array literal syntax is no longer sufficient and you have to fall back to imperative code, using a combination 
of push, splice, concat, etc. With spread syntax this becomes much more succinct:

```javascript
var parts = ['shoulders', 'knees'];
var lyrics = ['head', ...parts, 'and', 'toes']; 
// ["head", "shoulders", "knees", "and", "toes"]
```

###Copy an array

```javascript
var arr = [1,2,3];
var arr2 = [...arr]; // like arr.slice()
arr2.push(4); 

// arr2 becomes [1,2,3,4]
// arr remains unaffected
```

###A better push

push is often used to push an array to the end of an existing array. In ES5 this is often done as:

```javascript
var arr1 = [0, 1, 2];
var arr2 = [3, 4, 5];
// Append all items from arr2 onto arr1
Array.prototype.push.apply(arr1, arr2);
```

In ES2015 with spread this becomes:

```javascript
var arr1 = [0, 1, 2];
var arr2 = [3, 4, 5];
arr1.push(...arr2);
// arr1 is [0, 1, 2, 3, 4, 5] rather than [0, 1, 2, [3, 4, 5]]
// Instead, if we use arr1.push(arr2), arr1 become [0, 1, 2, [3, 4, 5]] instead of [0, 1, 2, 3, 4, 5] 
```


> Any argument in the argument list can use the spread syntax and it can be used multiple times

Example:

```javascript
function myFunction(v, w, x, y, z) { }
var args = [0, 1];
myFunction(-1, ...args, 2, ...[3]); //v: -1, w: 0, x: 1, y: 2, z: 3
myFunction(-1, ...args, 2, [3]); //v: -1, w: 0, x: 1, y: 2, z: [3]
```