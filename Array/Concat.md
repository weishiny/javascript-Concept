# javascript-Concept
Some reference for syntax and concept of javascript

##Array.concat()
Source: [JavaScript | MDN](https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Global_Objects/Array/concat)

The **concat()** method is used to merge two or more arrays. This method does not change the existing arrays, 
but instead returns a new array.

```javascript
var arr1 = ["a", "b", "c"];
var arr2 = ["d", "e", "f"];

arr1.concat(arr2);

// results in a new array [ "a", "b", "c", "d", "e", "f" ]
```

###Syntax
> var new_array = old_array.concat(value1[, value2[, ...[, valueN]]])

###Parameters
valueN
> Arrays and/or values to concatenate into a new array. See the description below for details.

###Return value
> A new Array instance.

##Example
###Concatenating two arrays
```javascript
var alpha = ["a", "b", "c"];
var numeric = [1, 2, 3];

alpha.concat(numeric);
// result in ['a', 'b', 'c', 1, 2, 3]
```

###Concatenating three arrays
```javascript
var num1 = [1, 2, 3],
    num2 = [4, 5, 6],
    num3 = [7, 8, 9];

var nums = num1.concat(num2, num3);

console.log(nums); 
// results in [1, 2, 3, 4, 5, 6, 7, 8, 9]
```

###Concatenating values to an array
```javascript
var alpha = ['a', 'b', 'c'];

var alphaNumeric = alpha.concat(1, [2, 3]);

console.log(alphaNumeric); 
// results in ['a', 'b', 'c', 1, 2, 3]
```