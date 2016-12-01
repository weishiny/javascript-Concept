# javascript-Concept
Some reference for syntax and concept of javascript

##Array.forEach()
Source: [JavaScript | MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/forEach)

The **forEach()** method executes a provided function once per array element.

```javascript
var a = ["a", "b", "c"];

a.forEach(function(element) {
    console.log(element);
});

// a
// b
// c
```

###Syntax
> arr.forEach(callback[, thisArg])

###Parameters
**callback**
Function to execute for each element, taking three arguments:    
    
- `currentValue`        
     - The current element being processed in the array.    
    
- `index`
     - The index of the current element being processed in the array.
    
- `array`
     - The array that forEach() is being applied to.      

**thisArg**  `Optional`
> Value to use as this(i.e reference Object) when executing callback.

###Return value
> undefined.

##Example
###Printing the contents of an array
The following code logs a line for each element in an array:

```javascript
function logArrayElements(element, index, array) {
  console.log('a[' + index + '] = ' + element);
}

// Notice that index 2 is skipped since there is no item at
// that position in the array.
[2, 5, , 9].forEach(logArrayElements);
// logs:
// a[0] = 2
// a[1] = 5
// a[3] = 9
```

###If the array is modified during iteration, other elements might be skipped.
The following example logs "one", "two", "four". When the entry containing the value 
"two" is reached, the first entry of the whole array is shifted off, which results in 
all remaining entries moving up one position. Because element "four" is now at an earlier 
position in the array, "three" will be skipped. forEach() does not make a copy of the array before iterating.

```javascript
var words = ["one", "two", "three", "four"];
words.forEach(function(word) {
  console.log(word);
  if (word === "two") {
    words.shift();
  }
});
// one
// two
// four
```
