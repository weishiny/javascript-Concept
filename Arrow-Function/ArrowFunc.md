# javascript-Concept
Some reference for syntax and concept of javascript

##Spread Operator
Source: 

- 1. [ES6 Arrow Functions: The New Fat & Concise Syntax in JavaScript](https://www.sitepoint.com/es6-arrow-functions-new-fat-concise-syntax-javascript/)
- 2. [ES6 arrow functions, syntax and lexical scoping](https://toddmotto.com/es6-arrow-functions-syntaxes-and-lexical-scoping/)

##What Are Arrow Functions?

Arrow functions – also called “fat arrow” functions, from CoffeeScript (a transcompiled language) are a more 
concise syntax for writing function expressions. They utilize a new token, **=>**, that looks like a fat arrow. 
Arrow functions are anonymous and change `the way this binds in functions`.


Arrow functions make our code more concise, and simplify function scoping and the this keyword. They are one-line 
mini functions which work much like Lambdas in other languages like C# or Python. (See also lambdas in JavaScript). 
By using arrow function we avoid having to type the function keyword, return keyword (it’s implicit in arrow functions), 
and curly brackets.

###Basic Syntax with Multiple Parameters 
```javascript
// (param1, param2, paramN) => expression 
 
// ES5 
var multiply = function(x, y) {
    return x * y;
}; 
 
// ES6 
var multiply = (x, y) => { return x * y }; //statement
```

The arrow function example above allows a developer to accomplish the same result with fewer lines of code 
and approximately half of the typing.

Curly brackets are not required if only one expression is present. The preceding example could also be written as:

```javascript
var multiply = (x, y) => x * y; //expression
```

> statement v.s expression

```javascript
//Source: [2]

/*ES5*/
// example 1
function ([param] [, param]) {
  statements
}

// example 2
function (param) {
  return expression
}

/****************************/

/*ES6*/
// example 1
([param] [, param]) => {
  statements
}

// example 2
param => expression
```

###Basic Syntax with One Parameter
Parentheses are optional when only one parameter is present

```javascript
//ES5 
var phraseSplitterEs5 = function phraseSplitter(phrase) { 
    return phrase.split(' '); 
}; 
 
//ES6 
var phraseSplitterEs6 = phrase => phrase.split(" "); 
 
console.log(phraseSplitterEs6("ES6 Awesomeness"));  // ["ES6", "Awesomeness"]
```

###No Parameters
Parentheses are required when no parameters are present.

```javascript
//ES5 
var docLogEs5 = function docLog() { 
    console.log(document); 
}; 
 
//ES6 
var docLogEs6 = () => { console.log(document); } 
docLogEs6(); // #document... <html> ….
```

###Object Literal Syntax
Arrow functions, like function expressions, can be used to return an object literal expression. 
The only caveat is that `the body needs to be wrapped in parentheses`, in order to distinguish 
between a block and an object (both of which use curly brackets).

```javascript
//ES5 
var setNameIdsEs5 = function setNameIds(id, name) { 
    return { 
        id: id, 
        name: name 
    }; 
}; 
 
// ES6 
var setNameIdsEs6 = (id, name) => ({ id: id, name: name }); 
 
(setNameIdsEs6 (4, "Kyle"));   // Object {id: 4, name: "Kyle"} 
```

###Use Cases for Arrow Functions
Now that we’ve covered the basic syntaxes, let’s get into how arrow functions are used.

One common use case for arrow functions is array manipulations and the like. It’s common 
that you’ll need to map or reduce an array. Take this simple array of objects:

```javascript
var smartPhones = [
	{ name:'iphone', price:649 },
	{ name:'Galaxy S6', price:576 },
	{ name:'Galaxy Note 5', price:489 }
];
```

We could create an array of objects with just the names or prices by doing this in ES5:

```javascript
// ES5
console.log(smartPhones.map(
    function(smartPhone) {
	    return smartPhone.price;
    }
)); // [649, 576, 489]
```

An arrow function is more concise and easier to read:

```javascript
// ES6
console.log(smartPhones.map(
	smartPhone=>smartPhone.price
)); // [649, 576, 489]
```

Here’s another example using the array filter method:

```javascript
var array = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15];

// ES5
var diVisibleByThreeES5 = array.filter(function(v) {
    return v % 3 == 0;
}); //[3, 6, 9, 12, 15]

//ES6
var diVisibleByThreeES5 = array.filter(v => v % 3 == 0); //[3, 6, 9, 12, 15]
```