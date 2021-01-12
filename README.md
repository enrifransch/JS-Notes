# JS Notes

## this
`this` is the object that a function is property of
```
const obj = {
	foo: 'bar',
	callMe() {
		return this;
	}
}
obj.callMe() // { foo: 'bar', callMe: [Function: callMe] }
```

## Closures
A closure is a function defined inside another function (called the parent function), and has access to variables that are declared and defined in the parent function scope.

```
foo() // undefined
bar() // 'bar
// Defined at run-time
var foo = function(){ 
    return 'foo'
}; 
// Defined at parse time
function bar(){ 
     return 'bar'
};

```

## Hoisting
Context variables declared using the `var` keyword or functions declared using the `function` keyword will have their declarations moved to the top of their scope or `lexical scope`, the global scope.  
>Global scope for: Browser (`window`) and Node (`global`)
>Declaring a variable with `let` or `const` does not add it to the global object.
```
foo() // undefined
bar() // 'bar
oop() // ReferenceError: Cannot access 'oop' before initialization
var foo = function(){ 
    return 'foo'
}; 
function bar(){ 
     return 'bar'
};
const oop = () => 'oop';
```
Above in the execution context, creation phase, `var foo` will be processed and a reference to `foo` will be created in memory with `undefined`

```
var favouriteFood = "grapes";

var foodThoughts = function() {
     console.log("Original favourite food: " + favouriteFood) // undefined
     var favouriteFood = "sushi";
     console.log("New favourite food: " + favouriteFood) // 'sushi'
}

foodThoughts()
```

## Strict Mode

>The short and most important answer here is that use strict is a way to voluntarily enforce stricter parsing and error handling on your JavaScript code at runtime. Code errors that would otherwise have been ignored or would have failed silently will now generate errors or throw exceptions. In general, it is a good practice.

- Makes debugging easier. Code errors that would otherwise have been ignored or would have failed silently will now generate errors or throw exceptions, alerting you sooner to problems in your code and directing you more quickly to their source.
- Prevents accidental globals. Without strict mode, assigning a value to an undeclared variable automatically creates a global variable with that name. 
```
function weird() {
	isWeird = 'yes';
	return isWeird;
}
weird() // 'yes'
```
- Eliminates `this` coercion. Without strict mode, a reference to a `this` value of null or undefined is automatically coerced to the global. In strict mode, referencing a a this value of null or undefined throws an error.
- Disallows duplicate parameter values. Strict mode throws an error when it detects a duplicate named argument for a function (e.g., function foo(val1, val2, val1){}), thereby catching what is almost certainly a bug in your code that you might otherwise have wasted lots of time tracking down.
-Makes eval() safer. There are some differences in the way `eval()` behaves in strict mode and in non-strict mode. Most significantly, in strict mode, variables and functions declared inside of an eval() statement are not created in the containing scope (they are created in the containing scope in non-strict mode, which can also be a common source of problems).
- Throws error on invalid usage of `delete`.  

## Misc
### IIFE (Immediately Invoked Function Expression)
(function() {
// variables declared will be scoped in this context
};)()
### Associativity rule 

Operators with the same precedence are processed based on the associativity property of the operator. The associativity of the assignment operator is Right to Left.

Number + Number -> Addition
Boolean + Number -> Addition
Boolean + Boolean -> Addition
Number + String -> Concatenation
String + Boolean -> Concatenation
String + String -> Concatenation

###  Check if object is array
 Object.prototype.toString.call()
 Array.isArray
 ### Get Modulus of negative
 ```
 function mod(n, m) {
  return ((n % m) + m) % m;
}
 ```
 ### Function Expression & Declaration
 ```
 // Function Expression
 const foo = () = {
	return 'foo';
}
 // Function Declaration
function foo() {
	return 'foo';
}
 ```
 ### Function Currying
 Currying is the technique of converting a function that takes multiple arguments into a sequence of functions that each take a single argument.
 ```
 sum(a+b+c)
 ```
 becomes
 ```
 sum(a)(b)(c)
 ```
This can be achieved either by using `bind` property or using `closures`.

```
// original
const sum = (a, b, c) => {
console.log(a + b + c)
}
// currying closure
const sumClosure = function (a) {
	return function(b) {
		return function (c) {
		console.log(a + b + c)
		}
	}
}
// currying generic

function curry(func) {
	return function curried(...args) {
		if (args.length >= func.length) {
			return func.apply(this, args);
		} else {
			return function(...args2) {
				return curried.apply(this, args.concat(args2));
			}
		}
};
}
```

this
bind
call
apply
generator
eval
prototype
<!--stackedit_data:
eyJoaXN0b3J5IjpbMjI3OTkyODU0LDE4NDc0NjM3MjcsMTEzNj
Q3MTYzLC01Mjg0NDM2NDgsNzU5NDc3NzgyLC03MjE3NzIwOTEs
LTQyNzg2MjgzNCwtMTE0NTcwMDEwOSwxMTMzNjQyMTMxLDYwMj
Y2ODIsMzIzOTIyNzgyLDIyNTQyMjQyMyw1NDIyMTkwNzMsMTQ4
NjMzMjY5NV19
-->