# javascript-Concept
Some reference for syntax and concept of javascript

##Currying
Source: [A Beginner’s Guide to Currying in Functional JavaScript](https://www.sitepoint.com/currying-in-functional-javascript/)

Briefly, currying is a way of constructing functions that allows partial application of a function’s arguments. 
What this means is that you can pass all of the arguments a function is expecting and get the result, or pass 
a subset of those arguments and get a function back that’s waiting for the rest of the arguments.

As an example, let’s imagine a function that greets somebody by name. We all know how to create a simple greet 
function that takes a name and a greeting, and logs the greeting with the name to the console:

```javascript
var greet = function(greeting, name) {
  console.log(greeting + ", " + name);
};
greet("Hello", "Heidi"); //"Hello, Heidi"
```

This function requires both the name and the greeting to be passed as arguments in order to work properly. But 
we could rewrite this function using simple nested currying, so that the basic function only requires a greeting, 
and it returns another function that takes the name of the person we want to greet.

```javascript
var greetCurried = function(greeting) {
  return function(name) {
    console.log(greeting + ", " + name);
  };
};

//This tiny adjustment to the way we wrote the function lets us create a new function for any type of greeting, 
//and pass that new function the name of the person that we want to greet:
var greetHello = greetCurried("Hello");
greetHello("Heidi"); //"Hello, Heidi"
greetHello("Eddie"); //"Hello, Eddie"

//We can also call the original curried function directly, just by passing each of the parameters in a separate 
//set of parentheses, one right after the other:
greetCurried("Hi there")("Howard"); //"Hi there, Howard"
```

###Curry All the Things!
The cool thing is, now that we have learned how to modify our traditional function to use this approach for dealing 
with arguments, we can do this with as many arguments as we want:

```javascript
var greetDeeplyCurried = function(greeting) {
  return function(separator) {
    return function(emphasis) {
      return function(name) {
        console.log(greeting + separator + name + emphasis);
      };
    };
  };
};
```

We have the same flexibility with four arguments as we have with two. No matter how far the nesting goes, we can create 
new custom functions to greet as many people as we choose in as many ways as suits our purposes:

```javascript
var greetAwkwardly = greetDeeplyCurried("Hello")("...")("?");
greetAwkwardly("Heidi"); //"Hello...Heidi?"
greetAwkwardly("Eddie"); //"Hello...Eddie?"

//What’s more, we can pass as many parameters as we like when creating custom variations on our original curried function, 
//creating new functions that are able to take the appropriate number of additional parameters, each passed separately in 
//its own set of parentheses:
var sayHello = greetDeeplyCurried("Hello")(", ");
sayHello(".")("Heidi"); //"Hello, Heidi."
sayHello(".")("Eddie"); //"Hello, Eddie."

//And we can define subordinate variations just as easily:
var askHello = sayHello("?");
askHello("Heidi"); //"Hello, Heidi?"
askHello("Eddie"); //"Hello, Eddie?"
```

